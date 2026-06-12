---
title: "Lilo booting directly into ubuntu"
date: 2005-06-03
forum: Desktop Environments
---

### Post by xo310 on 2005-06-03
Hi,
I &#305;nstalled ubuntu on a third partition on my harddisk and everything went fine until GRUB installation failed. I saw the lilo option after that grub fatal error message. Lilo installed correctly and installation continued to the end.
Now when i restart my pc lilo boots directly into ubuntu without displaying winxp option. I searched in the forum and found that there is lilo.conf to work with but could not get it to work.
Note: I ran command>>lilo after every change.

here is lilo.conf


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
boot=/dev/hda

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/hda5

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
vga=normal

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
other=/dev/hda
	label=Windows
#	restricted
#	alias=2


any idea?
thanks

---

### Post by tdjokic on 2005-06-03
> # If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
# label=HURD
# restricted
# alias=3
other=/dev/hda
label=WindowsYour problem is on this line "other=/dev/hda" - you must specifie number of partition Windows is on, like in example "# other=/dev/hda4". It is hda1 probably?

---

### Post by xo310 on 2005-06-03
I did try this but did not work.
Am I running lilo wrongly? I open the "root terminal" and from there type "lilo" right?
then restart. This is what i am doing.

I also commented the line saying: "default=linux" but no effect.
Dont know why grub failed to install in the first place

---

### Post by xo310 on 2005-06-03
here is what i get when i run lilo

root@ubuntu:/home/semose # lilo
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/hda1'
Added Linux *
Skipping /vmlinuz.old
Warning: CHANGE AUTOMATIC assumed after "other=/dev/hda1"
Added Windows
root@ubuntu:/home/semose #

---

### Post by xo310 on 2005-06-03
can i just uninstall lilo and try to install grub using synaptic? if yes then what is the appropriate sequence to do it?
thanks

---

### Post by tdjokic on 2005-06-03
[http://www.ubuntuforums.org/showthread.php?t=38625](http://www.ubuntuforums.org/showthread.php?t=38625) here is something like your problem with grub

---

