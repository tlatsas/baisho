# About

baisho is a bash wrapper over dd and cdrkit with a cool name,
it provides a simple interface to :

* burn iso images to discs (using wodim from cdrkit)
* rip discs to iso images (using dd)

the idea was taken from the Linux Journal article:

[Archiving CDs to ISO from the Command Line] [1]

[1]: http://www.linuxjournal.com/content/archiving-cds-iso-commandline


# Synopsis

    usage: baisho [ OPTIONS ] [ rip | burn ] <image>


# Description

A bash wrapper over dd and cdrkit to burn/rip ISO images


# OPTIONS
    -h    Show this message
    -l    List available optical devices
    -d    Device target to use as CD/DVD
    -s    Show md5 checksums of disc and image after burn or rip

# OPERATIONS

    rip <image>
    burn <image>

# Examples

* burn image "sample.iso", using the optical device /dev/sr0

code:

    baisho -d /dev/sr0 burn "sample.iso"

* burn image "sample.iso"

code:

    baisho burn "sample.iso"

If no device is explicitly specified and there are multiple devices in the system
then user is prompted to select. If there is only one system device then it is used
by default.


* rip from default system device in /tmp/img.iso

code:

    baisho rip "/tmp/img.iso"

If image already exists then user is prompted to overwrite.

* rip from /der/sr0 to /tmp/img.iso and calculate checksums

code:

    baisho rip -s -d /dev/sr0 "/tmp/img.iso"

* list all system optical devices reported by udisks

code:

    baisho -l

