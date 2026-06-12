---
title: "Kernel updates: how do they work?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by MikeMLP on 2006-07-18
Greetings!
I recently got the following update through Synaptic: 

linux-image-2.6.15-26-386 (2.6.15-26.44) to 2.6.15-26.45

But upon restarting, uname -r shows this:

```
mike@Ubuntu:~$ uname -r
2.6.15-23-386
```

I am currently booting using lilo on my linux partition (I chainload Lilo using a GAG boot disk).  I am guessing that I need to change some configuration file so that it boots using the new Kernel instead of the old one (which I suppose I should use since the releaselogs mention a critical security fix).

How can I go about doing this?  Can I delete the old kernel(s) once I am successfully booting into the new one?  What about the 686 version?  I have downloaded that version as well, but havn't figured out how to boot into it.  I am assuming that the procedure would be similar.  

Thanks for any tips you can give.

---

### Post by Ramses de Norre on 2006-07-18
I guess we could figure this out of you post your lilo config file, and is there any particular reason why you don't use grub? It's far easier..

---

### Post by MikeMLP on 2006-07-19
Oddly enough, my lilo.conf is being called lilo.conf.0, so I had a hard time finding the file:

```
 mike@Ubuntu:~$ lilo
/etc/lilo.conf: No such file or directory

``` (don't ask me how this machine is able to boot at all...)

The file reads as follows:

```
# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/hda5

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/hda5

# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=20

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#	prompt
#	delay=100
#	timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#


# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1

	initrd=/initrd.img

image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
#	restricted
#	alias=2

	initrd=/initrd.img.old


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3
other=/dev/hda2
	label=Windows
#	restricted
#	alias=2
other=/dev/hda1
	label=Windows1
#	restricted
#	alias=2

```

And to answer your question: The decision to use Lilo over grub was a complex one for me.  First, I didn't want my MBR to be touched and risk messing up my Windows partition.  While I realize that both Lilo and Grub can be installed in the Linux partition, I could not find any documentation (when planning my installation) that said explicitly that a GAG boot disk could chainload grub, but I did find explicit information that said that GAG could chainload Lilo.  Therefore, for my purposes at the time, Lilo was the logical choice because as a complete newbie, I determined that it would give me my greatest chance of success while leaving my windows half completely untouched.

Finally, while looking through the commented sections of the file, I'm thinking it has something to do with these lines:
```
# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
```

-goes to find documentation-
In the mean time, if you have any suggestions, feel free to post.

Thanks!
 - Mike

---

