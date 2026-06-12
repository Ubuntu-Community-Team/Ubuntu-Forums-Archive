---
title: "Fd0 boot load problem."
date: 2009-04-27
forum: General Help
---

### Post by maskedmakrel on 2009-04-27
Hello, I am new to the Ubuntu forums and to the Ubuntu OS.

I am using 9.04.  I am trying to run Ubuntu on an HP NC6000 notebook.  No default bios setting.  [The primary HD melted (MBR still works) so I want to use a USB boot].

I used Plop to modify the MBR to allow for a USB boot and using the Live CD created a USB disk with a substantial partition for persistency.

The LIVE CD boots well but I want something a bit more persistent.  Don't want to install flash everytime, for example.

The only thing is that when I try to boot off the USB, I get a series of I/O errors as it looks for FD0.  It takes forever.  The same disk will boot in no time on a Dell Inspiron 1525, but not on the HP NC6000.

I have tried several pen variants but they all end up the same.  (PortableLinux, for example), so I's sticking with the default USB maker included in the menu.

When I try to load, I get the:

end_request:  I/O error, dev fd0, sector 0

I have tried several cures:

1.  I modified my bios as much as possible.

(The NC6000 uses a multibay which means the CD/Floppy are interchangeable.  I'm currently using the CD).  I have removed the CD DRIVE and left the bay empty, nothing.  I do not have the floppy component.  So don't ask.  

There is nothing left for me to try to modify on this front.

2.  I tried to create a blacklist file in the etc/modprobe.d/blacklist sense as per other threads:  

[https://answers.launchpad.net/ubuntu/+question/7697](https://answers.launchpad.net/ubuntu/+question/7697)

This did not help.

My blacklist file currently reads:

blacklist floppy

The stated solution was to do this:

sudo kate /etc/modprobe.d/blacklist
 and add this at the end:
 # floppy driver since I don't have one
blacklist floppy
 Also, if in the file /etc/fstab there is an entry like this:
 /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

I had no blacklist file in the directory, so I created a text version and copied it to the folder.  As for the fstab, I did not have that entry, so I ignored.  This has not helped.

Is it supposed to read

fd0 blacklist floppy? or just blacklist floppy? or something else.

3.  I hear that expert boot might help, but still I get nothing.

A friend of mine wrote me that:

"Sometimes it may be necessary to blacklist a module to prevent it from
being loaded automatically by the kernel and udev. One reason could be
that a particular module causes problems with your hardware. The
kernel also sometimes lists two different drivers for the same device.
This can cause the device to not work correctly if the drivers
conflict or if the wrong driver is loaded first.

You can blacklist a module using the following syntax:
module_name.blacklist=yes. This will cause the module to be
blacklisted in /etc/modprobe.d/blacklist.local both during the
installation and for the installed system.

Note that a module may still be loaded by the installation system
itself. You can prevent that from happening by running the
installation in expert mode and unselecting the module from the list
of modules displayed during the hardware detection phases."

****I tried to select expert mode at boot, but nothing changed.


4.  I tried to add the following to the boot option with F6

"all_generic_ide"

They said I should add to end, but does that come after the two dashes --

In any case, I added it at the end and nothing happened.

Hardware:

HP NC6000
1.80 Intel Pentium M
1 gb ram
ATI Mobility Radeon 9600 (32 MB)
4 gb Geeksquad USB drive
Atheroes AR5100X+Wireelss Network Adapter
Broadcom Corporation NetXtreme BCM57y05M_2 Gigabite Ethernet (rev. 03)

Thanks.

---

### Post by wolfen69 on 2009-04-27
i believe you can add (only) **fd0** to /etc/modprobe.d/blacklist

i don't believe you need to specify **blacklist fd0** because it is a given that anything in the blacklist file is to be blacklisted.

---

### Post by maskedmakrel on 2009-04-27
@Wolfen

So file currently simply reads:

blacklist floppy

Nothing more.  But you think I don't need to add anything else?

In any case it did not work, it still takes about 30 minutes to boot up because of the i/o fd0 error.

---

### Post by wolfen69 on 2009-04-27
do NOT put **blacklist floppy** as the entry. just put **blacklist fd0** as the entry in the blacklist file.

---

### Post by maskedmakrel on 2009-04-27
@Wolfen69

I replaced it with your suggestion and it made absolutely no difference unfortunately.

I am still getting really long boot times and the same I/O error.

Knoppix install works like a breeze, but the default package and installer are much weaker, so I'm hoping Ubuntu can pull through on this.

---

