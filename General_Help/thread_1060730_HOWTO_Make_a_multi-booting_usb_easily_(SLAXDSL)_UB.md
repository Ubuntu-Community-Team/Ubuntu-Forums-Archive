---
title: "HOWTO: Make a multi-booting usb easily (SLAX/DSL) UBUNTU 8.10"
date: 2009-02-05
forum: General Help
---

### Post by arkticcool on 2009-02-05
[COLOR="Red"]This HOWTO does not come with any guarantee, use at your own risk.[/COLOR]

Tutorial created on Ubuntu 8.10.

I have searched long and hard on how to make a multi-booting USB, and HURRAH I finally found my holy grail. Its called Mk-boot-USB, a PERL script that can be found at [http://people.ofset.org/~ckhung/p/mk-boot-usb/](http://people.ofset.org/~ckhung/p/mk-boot-usb/). Use at your own risk, I and the author of Mk-boot-USB take no responsibility for the consequences resulting from improper use of this script. 

Your USB for this tutorial must exceed 1GB in size.

You must install qemu to quickly test your USB's bootability (invented adj). 
To install qemu type in:

```
 sudo apt-get install qemu
```

And follow the prompts.

[COLOR="Red"]YOUR USB MUST BE UNPLUGGED BEFORE BEGINNING THIS TUTORIAL.

YOUR USB WILL BE REPARTITIONED BY THIS TUTORIAL, BACK UP ALL FILES ON THE USB, THEY CANNOT BE RESTORED.[/COLOR]

Download the latest version and place it into root ( / ). Can't access root? Go to terminal (Apps -> Accessories -> Terminal) and type in:

```
sudo nautilus
```

And use that window to copy to root ( / ).

Once this is done, type in:

```
gconf-editor
```

In the new window that opens up, go to (Nautilus -> Preferences) and uncheck media_automount and media_automount_open.

Go back to terminal and type in:

```
sudo bash
```

This then puts you in root, be careful when in this state.

Now type in:
```
  
        cd /
        tar xzf ~/mk-boot-usb-08h.tgz
        mk-boot-usb

```

This changes the directory to root ( / ), extracts the tar and executes the script.

When a dialog pops up asking you to insert the USB, insert it.
Make sure it is the correct usb. 

If Nautilus opens a window and the usb is mounted, discontinue this tutorial, and disable auto-mount properly.

[COLOR="SeaGreen"]This tutorial only shows how to install DSL (Damn Small Linux ) and SLAX (Slackware based Live distro). A further tutorial will be made on how to install Ubuntu 8.10, BT3 (Back Track 3), Ophcrack xp-vista, NTPasswd, Parted Magic, Smart boot manager, Super Grub Disk, VistaPE, XP-PE.[/COLOR]

Once the USB has stopped flashing press enter, Mk-boot-usb will now display the usb storage device, its size, parent directories and files, along the lines of what is displayed below:

```

=+=+= 	Insert the usb stick, wait a few seconds (often the usb stick
=+=+=   will flash a bit), and press enter to continue. If file manager(s)
=+=+=   pops up, please press control-C to abort and read the web pages
=+=+= 	about disabling automatic mounting.

=+=+= Your usb stick has these partitions: /dev/sdX /dev/sdX1
=+=+= The most recently modified few files in each partition are:
mount: you must specify the filesystem type
=+=+= [ /dev/sdX ]
total 0
umount: /tmp/mk-boot-usb/mnt/sdX: not mounted

=+=+= [ /dev/sdX1 ]
total 4
drwxr-xr-x 5 root root 4096 2009-02-02 20:34 RANDOM FOLDER

=+=+= size of destination stick /dev/sdX: 3839 MB
=+=+= partition 4 using 16 MB; 3823 MB available for other partitions

=+=+=     Type in a list of numbers separated by spaces representing
=+=+=     the sizes of each partition in MB. For example:
=+=+= 	    3523 60 240
=+=+=     means 1 fat and 2 ext2 partitions, each of size 3523, 60, 240 MB.
=+=+=     Sizes: 

```

There are two choices here (but only one will be followed in this tutorial). You can use the predetermined 3523 60 240, or you can set your own (next tutorial). Set the predetermined number calculated by Mk-boot-usb and type in yes when prompted. The partitions shall be made (16MB for booting (tyylinux/grub), a vfat and two ext2 paritions 60 and 240 MB in size) and the USB will have ttylinux (basic linux distro) and grub (bootloader ) installed on it. 

Now to test the usb. Leave it in, and in terminal type in:

```
qemu -usb /dev/sdX 
``` 

Where X is a variable from USB to USB, you should have seen it in the Mk-boot-USB initial file display.

If your USB boots into ttylinux follow the following steps.

Download both DSL and SLAX (LIVECD VERSIONS i.e. ISOs) from [http://damnsmalllinux.org/](http://damnsmalllinux.org/) and [http://www.slax.org/](http://www.slax.org/) respectively.

Place them in root ( / ) with:
```
 sudo nautilus 
```

In addition to copying the ISOs, whilst in a super Nautilus create two directories under /media in root( / ) called tmp5 and tmp6.

When this is all completed type in the following commands:

```

        cd /
        mount -o loop dsl-4.2.5.iso /media/cdrom
	mount /dev/sdX5 /media/tmp5
	cd /media/cdrom
	cp -a . /media/tmp5
	umount /dev/sdX5

```

Substituting the X for your respective USB and dsl-4.2.5.iso with the name of your ISO (it may be different).

For the slax install do the following:
```

        cd /
        mount -o loop slax6.0.9.iso /media/cdrom
	mount /dev/sdX6 /media/tmp6
	cd /media/cdrom
	cp -a . /media/tmp6
	umount /dev/sdX6

```


Once again substituting the X for your respective USB and slax6.0.9.iso with the name of your ISO (it may be different).

Once this is done, delete tmp5 and tmp6 and once again test your usb with the following:

```
qemu -usb /dev/sdX
```

If all has gone according to plan, your USB will boot into SLAX and DSL no sweat. If you would actually like to boot your USB, take it out, reboot, go to BIOS, change the boot order for USB first and save and exit. Plug your USB in and it should boot.

Have fun with your computer on a stick. Leave comments, and maybe a few thanks :P.

---

### Post by clay_glenn on 2009-03-15
I've had some success, but sometimes it isn't obvious what to put into the GRUB menu.lst file to get it to work right.  I copied the files from the Ubuntu Live CD into a partition, and managed to get it working by copying the Edubuntu example that is already sampled in the menu.lst file.  But when I put Puppy Linux Live CD files into another partition, I never did get it to work.  It always fails trying to find pup-412.sfs, even though it is in the same partition location as the other Puppy Linux files.

I've searched lots of forums, but can't get it to work right for some reason.

Since the Live CDs normally have their own boot loader built in, how do you get it to work correctly with GRUB on a multi-partition USB stick?

---

