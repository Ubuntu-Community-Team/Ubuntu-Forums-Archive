---
title: "VirtualBox Newbie Questions"
date: 2010-09-24
forum: Desktop Environments
---

### Post by pbhill on 2010-09-24
I have been using Ubuntu for a few years, but still dual boot into XP for a couple of key programs. I find that my XP installation is corrupt and I need to reinstall. This looks like a good time to ask if it makes sense to install XP in VirtualBox rather than on a separate partition. Rebooting all the time is a a pain. I have tried VB but only with other Linux Distos. Do I still need to have all those pesky Microsoft Updates? What happens when I upgrade Ubuntu? I can't risk losing any data. Can anyone point me in the right direction here?

---

### Post by cocopuffz on 2010-09-25
Yes. You'll still need to install the windows updates in the virtual machine version of Windows... make sure you use the non OSE version of virtualbox. You can't use USB in the OSE version. I suspect that if you plan on using windows in a vm, you're going to want to have it replace a full machine with all a full machines functions.

If you want dx9 support, start your win vm in safemode when you install guest additions.

I even defrag my vm's.

---

### Post by howefield on 2010-09-25
> **pbhill said:**
> Do I still need to have all those pesky Microsoft Updates?

Your VM will think it is a "real" installation, and will behave as if it were, and so will need to be treated like one with regard to not only updates, but protection and housekeeping also.

> What happens when I upgrade Ubuntu? I can't risk losing any data.

Nothing will happen when you upgrade Ubuntu, at least not to your VM, but would you lose your only copy of valuable data if your hard disk died ? If yes, then you need to revisit your backup strategy.

---

### Post by linux4me on 2010-09-25
All your Virtual Box settings and the "machines" you create (your installations of various OSs) reside in a hidden folder called ".VirtualBox" in your home directory, so if you back up your home directory regularly using a program (like rsync/grsync) that catches hidden folders, you will have a backup of your Winblow$ installations. It does take a while to back up these folders. It is the slowest part of my backup, so much so that I only back them up periodically.

I've been using Virtual Box with Ubuntu for years, and now have an XP installation and a Win 7 installation for a couple of programs that just don't have Linux equivalents. (I feel dirty every time I run Windoze, but I can't get rid of them. They're for work.) Virtual Box is far superior to a dual boot situation as long as you can run the programs you need in that environment for exactly the reason you describe; no need to reboot. For gaming, I wouldn't recommend it as 3D graphics can be problematic. Your host machine also needs to be more robust than it would for a dual boot as you are sharing RAM and video memory in the VM.

You'll probably get a better idea if switching to Virtual Box makes sense if you list the programs you plan to run in it. People here can give you an idea of how well they run.

---

### Post by pbhill on 2010-09-26
linux4m3 wrote:  "You'll probably get a better idea if switching to Virtual Box makes sense if you list the programs you plan to run in it. People here can give you an idea of how well they run."

The only windows programs I really need are:
      Quickbooks
      Chief Architect
      Sketch Up

My daughter has some online stuff for school that is only available using Internet Explorer.

Will the sharing of RAM and video memory affect Ubuntu or just the OS running in VB?

Thanks for all the suggestions!

---

### Post by linux4me on 2010-09-26
Yes, sharing the RAM and video RAM will affect both the host OS (Ubuntu) and the guest OS (Winblows) while the guest OS is running in Virtual Box. I really don't notice a troubling amount of slowdown though, and I have an Intel Core 2 system with 4 GB of RAM (2 GB allowed to Win XP in Virtual Box) and just a wimpy Nvidia 7800 GS with 256 MB of RAM (128 MB allowed to the guest OS). If I'm running something in one or the other that takes a lot of processing, switch to the other and try to do the same, I notice a difference, but that doesn't happen often. I'm usually only working in one or the other so it's really not an issue. It's *way* less annoying than having a dual-boot setup.

You can adjust the amount of resources you give the guest OS with Virtual Box, by the way.

I'm not familiar with Chief Architect or Sketch Up, but if they require 3D graphics you may have some issues with Virtual Box. The nice thing is that you can give it a try before you remove your dual-boot setup and if it doesn't work out just delete the virtual machines and uninstall Virtual Box.

---

### Post by Dr. C on 2010-09-27
One suggestion when running Microsoft Windows in VirtualBox to not activate Windows until the guest additions are installed in VirtualBox and one has finalized how the VM will look, namely ram video ram etc. 
As for applications 2D applications such as Quickbooks will run just fine 3D applications there is limited support Direct X 9 and Direct X 10 (experimental) 
As mentioned before, the installation of Windows in the VM will need all the TLC a Windows installation requires, anti-virus, defragmentation, updates etc. 
As for the version of VirtualBox it comes down to USB support in the guest. If one needs USB support in the gust go with PUEL, if not go with OSE.

---

### Post by pbhill on 2010-10-02
Thanks for all the advice. I'm running XP in VirtualBox, and I'd almost say it runs better than it did in a standalone installation!
  The problem I am having however is in VB. I can't for the life of me get a connection with my USB hard drive or network with the rest of my system. It does see my USB printer and my iPod. (But my music library is on the USB drive!) I've read all I could find and Googled it to death, but there seems to be no good answer that isn't overly technical. Can anyone out there point me towards a tutorial or some thing written for an average user?

---

### Post by Nxu5 on 2010-10-02
Sorry to cut in here, but when I first switched to Ubuntu I used VB, and my experiences are that you should set as many virtual USB ports as you need/as your actual desktop/laptop has.

Hope that helps :D

---

### Post by nlsthzn on 2010-10-02
> **pbhill said:**
> Thanks for all the advice. I'm running XP in VirtualBox, and I'd almost say it runs better than it did in a standalone installation!
  The problem I am having however is in VB. I can't for the life of me get a connection with my USB hard drive or network with the rest of my system. It does see my USB printer and my iPod. (But my music library is on the USB drive!) I've read all I could find and Googled it to death, but there seems to be no good answer that isn't overly technical. Can anyone out there point me towards a tutorial or some thing written for an average user?

Not sure about this but I read somewhere in another thread that USB does not work in Virtualbox OSE... However have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=341740"), might help...

---

### Post by linux4me on 2010-10-02
I think that in this case the OP is trying to access music on a USB external drive, so he's not actually subject to the OSE/PUEL VB version thing. What he probably needs to do is add the folder where the music is (/media/<his drive UUID>) as a shared folder in VB, since it should be automatically mounted on the host system when he plugs the drive in.

In VB before you start the Win XP virtual machine (VM), click your VM to select it, then click Settings -> Shared Folders -> Add Shared Folder (the top icon on the right) -> click the down arrow by Folder Path -> select "Other" -> File System -> media, and see if you can browse to your USB drive, which should be in /media.

---

### Post by cocopuffz on 2010-10-03
This thread helped me a while back when usb wasn't working properly

[http://www.uluga.ubuntuforums.org/showthread.php?t=1445314&page=3](http://www.uluga.ubuntuforums.org/showthread.php?t=1445314&page=3)

---

### Post by pbhill on 2010-10-03
> **linux4me said:**
> 

In VB before you start the Win XP virtual machine (VM), click your VM to select it, then click Settings -> Shared Folders -> Add Shared Folder (the top icon on the right) -> click the down arrow by Folder Path -> select "Other" -> File System -> media, and see if you can browse to your USB drive, which should be in /media.

This sounds good, but after I choose my folder on the USB drive, the OK button remains grayed out. Same as the grayed out USB connections...

---

### Post by oregonbob on 2010-10-03
If it is greyed out, you probably have the USB drive mounted and accessed in linux. Do a "mount" command to see if linux automounted it as it normally does. Right-click in linux, unmount it, then attach it in XP. I do it all the time. I have tried all kinds of USB devices and all work. I'm using the Oracle version of VirtualBox.

You can even run a little script and have it automatically start Windows XP in a separate deskview on boot up. Here is a little perl script that starts VirtualBox and Windows-XP virtual machine in screen 3, then pops back to screen one.

> #!/usr/bin/perl
use strict;
use warnings;
system("wmctrl -s 2");
system("VBoxManage startvm Windows-XP");
system("wmctrl -s 0");

I adapted that script from another older post. Love how it automatically starts my XP.

---

### Post by pbhill on 2010-10-04
Thanks Oregonbob! That was the answer! When I unmounted my USB hard drive from the host (Ubuntu) and enabled it in the guest (XP) all the other USB devices magically followed suit. I even have Bluetooth again. The only problem was my wireless mouse. I lost that, but finally figured out that it needed to stay with Ubuntu. Go figure.
I will have to try that script, but I've been through enough for one day!

---

