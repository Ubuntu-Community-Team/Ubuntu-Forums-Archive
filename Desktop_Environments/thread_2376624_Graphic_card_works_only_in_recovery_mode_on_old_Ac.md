---
title: "Graphic card works only in recovery mode on old Acer Aspire One 105"
date: 2017-11-04
forum: Desktop Environments
---

### Post by aglessi on 2017-11-04
I've just installed lubuntu 17.10 on an old ACER Aspire One Notebook (model A 105 - Intel Atom N270). I'm rather satisfied by performance and I'd like to keep it, but I have an issue that I don't know how to solve. Everything works fine only if a start from the recovery partition and then I select to start with Ubuntu, otherwise the graphic card isn't properly initialized and I can see only a small portion of the desktop while the rest of the screen is full of garbage (as it happens when the proper resolution or frame rate aren't correct). As I wrote before the problem doesn't appear if I start from the recovery partition. I am almost a linux newbie and I don't know where to look to try to address this issue. Thanks for any hint.

---

### Post by gianlo on 2017-11-04
Same problem with MSI U123H (Atom N280), i've also try to install intel driver but nothing changes

---

### Post by gianlo on 2017-11-04
Also try this Work-around:
Edit (or create) /etc/X11/xorg.conf as follows: (there should be a tab before each line except the first and the last).
Section "Device"
Identifier "Intel Graphics"
Driver "intel"
Option "AccelMethod" "uxa"
EndSection

Nothing

And also conveting installation from lubuntu to xubuntu doesn't works

Graphic card works only in recovery mode why ?

---

### Post by ajgreeny on 2017-11-04
Can you check that you have the **xserver-xorg-video-intel** package installed.

There was a time in one of the versions of Lubuntu where it was  missing and caused problems.

Run command ```
dpkg -s xserver-xorg-video-intel
``` to see what is installed at present.

---

### Post by aglessi on 2017-11-04
> **ajgreeny said:**
> Can you check that you have the **xserver-xorg-video-intel** package installed.

There was a time in one of the versions of Lubuntu where it was  missing and caused problems.

Run command ```
dpkg -s xserver-xorg-video-intel
``` to see what is installed at present.

Not installed on my system.
I'll try to install it and I'll let you know.
Thanks

---

### Post by gianlo on 2017-11-04
Yes, I had forgotten ti write, i have also xserver-xorg-video-intel package installed

---

### Post by gianlo on 2017-11-04
> **ajgreeny said:**
> Can you check that you have the **xserver-xorg-video-intel** package installed.

There was a time in one of the versions of Lubuntu where it was  missing and caused problems.

Run command ```
dpkg -s xserver-xorg-video-intel
``` to see what is installed at present.

Checking with whis command i notice that Priority is optional, maybe is this the problem ?

---

### Post by aglessi on 2017-11-04
Tried to install server-xorg-video-intel via apt-get but I've got a message saying that was already present and updated to the latest version available. Now I'm confused even more than before...

---

### Post by gianlo on 2017-11-05
What is the difference of video drivers between recovery mode and normal mode?

---

### Post by ajgreeny on 2017-11-05
Recovery mode does not use the normal drivers but fbuffer I believe, which whilst it works, has low level capabilities.

---

### Post by gianlo on 2017-11-05
Any idea for solve ?

---

### Post by mörgæs on 2017-11-06
As can be seen here there is attention on the problem:

[https://ubuntuforums.org/showthread.php?t=2376580](https://ubuntuforums.org/showthread.php?t=2376580)

There are some workarounds mentioned in the Launchpad thread, else I suggest staying with 17.04 for some time.

---

### Post by aglessi on 2017-11-06
Don't know if could be of any help but I have tried to connect an external monitor to the netbook using the VGA port on its side. Well, it works... the desktop appears without any of the referred issues and everything is fine. The external monitor remains blank and I don't have found a way to manage it. Just inserting a VGA plug doesn't work, the external monitor has to be connected and plugged in.

---

### Post by gianlo on 2017-11-07
I have also try this, but without solve the problem

sudo nano /etc/default/grub

 Simple editor 'nano' will open.
Add line
GRUB_GFXPAYLOAD_LINUX=text
at the end of file.

 Save file and exit from nano.
 issue command:
 sudo update-grub

 reboot.

---

### Post by andrewm88 on 2017-11-07
> **mörgæs said:**
> As can be seen here there is attention on the problem:

[https://ubuntuforums.org/showthread.php?t=2376580](https://ubuntuforums.org/showthread.php?t=2376580)

There are some workarounds mentioned in the Launchpad thread, else I suggest staying with 17.04 for some time.

I'm also completely new to ubuntu, having the same issue running lubuntu 17.10 on a netbook with the intel atom n270 chipset. I've been using it with the nomodeset command added to the grub, but it means im stuck in 600x800 resolution.

When you say stay with 17.04, is there any way to rollback to an older distro or do I have to make a new iso and wipe the system?

Sorry if these are stupid questions!

---

### Post by mörgæs on 2017-11-08
I would not say stupid but you could probably have found the answer by googling.
There is no way to roll back a release. Just do a fresh install (which I also recommend when rolling forward).

---

### Post by gianlo on 2017-11-12
This fix the problem:

edit /etc/default/grub and add this line in the end of file
GRUB_GFXPAYLOAD_LINUX=text

Than: sudo update-grub
reboot

---

### Post by aglessi on 2017-11-12
Tried to edit the file invoking a shell with root privileges from the recovery menu, but it says that I has no write permission for that file. Any workaround?

---

### Post by gianlo on 2017-11-16
Try this:
sudo nano /etc/default/grub

---

### Post by markn2wa on 2018-02-17
Sorry if I mess this this up, this is my fires post here!

Thank you very much for your solution as I had the EXACT same problem with my GATEWAY net-book

(an LT2016U).

I am using Lubuntu 17.10.1 with the same issue (evidently using the same graphics card).

I edited the GRUB file using the ABIWORD program that was installed and followed your instructions.

My FIRST GRUB edit! and I did NOT mess things up (pretty good for a newbe!)

Thank you again! Mark T.

---

### Post by wildmanne39 on 2018-02-17
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by piwikiwi on 2018-03-27
> **gianlo said:**
> This fix the problem:

edit /etc/default/grub and add this line in the end of file
GRUB_GFXPAYLOAD_LINUX=text

Than: sudo update-grub
reboot
Hi there, 
I have this problem too.

How did you do the editing with only 1/5 of a usable screen?
Clueless win10 convert. Help! Please :)

---

### Post by piwikiwi on 2018-03-27
Update:

so once I’m in Recovery mode, it looks okay. But how (step by step please) do I correctly edit to fix the problem?

I tried the fix on the previous page, but its not working for me, could easily be I’m doing it wrong....

Thanks for any help.

---

### Post by mörgæs on 2018-03-27
> **piwikiwi said:**
> 
I tried the fix on the previous page, but its not working for me, could easily be I’m doing it wrong....


If you want us to help from here you need to tell us the exact commands you used and their results, preferrably with copy-paste from the command line.

---

