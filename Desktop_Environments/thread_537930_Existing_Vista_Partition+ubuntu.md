---
title: "Existing Vista Partition+ubuntu"
date: 2007-08-29
forum: Desktop Environments
---

### Post by darkhacker902 on 2007-08-29
Ok, So I would like to use My Windows vista Home premium OS in Ubuntu. 

Its 126 GBs (and my ubuntu partition is 11 GBs, Which I cant seem to fix....:| ) 

I would like to do the following but dont know how:

Edit my partition so that I can have atleast 100 GBs on my Ubuntu Partition.

Use Windows vista in ubuntu, so that I can run certain programs that are not compatible in wine and etc.


Im Really tired of having to go into vista when I need it. Id like it to be right there.

I have qtparted installed, Vmware player, but dont know how to use it, and VirtualBox, and dont know how to use it either.


When I try and use QTparted, it says I need to unmount the volume first, so I go to do that, then it gives me an error, so I go to the NTFS configuration tool, select enable write support for internal deices (Because I want to read/write to them, and It unmounts the volume) 

and it gives me this error:


> Mounting /media/hda1 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/86126BF0126BE421': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/disk/by-uuid/86126BF0126BE421 /media/hda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/disk/by-uuid/86126BF0126BE421 /media/hda1 ntfs-3g defaults,force 0 0

---

### Post by kellemes on 2007-08-29
From virtualbox-manager you can start a new guestOS, from this manager you need to mount the Windows-installCD and install Windows within the virtual space.
Don't forget you can't do everything you normally can when you run Windows, for example.. you won't be able to install the proper driver for your videocard, and so.. probably not be able to run a lot of games..
Virtualbox also includes the guestadditions-package I believe, you should install those.

---

### Post by darkhacker902 on 2007-08-29
oh. Well then what can I do to play games?

---

### Post by kellemes on 2007-08-30
Well, the app. database at WineHQ.com does list games you can get running on GNU/Linux.
[Cedega]("http://www.transgaming.com/") is an option..
But the easiest way to get Window games running is starting-up Windows.
Dualboot that is..

---

