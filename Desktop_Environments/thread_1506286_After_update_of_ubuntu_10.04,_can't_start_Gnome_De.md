---
title: "After update of ubuntu 10.04, can't start Gnome Desktop after login"
date: 2010-06-10
forum: Desktop Environments
---

### Post by vanchope on 2010-06-10
Hi,

I use ubuntu 10.04 in VirtualBox (upgrated from 09.10), host os is Win7.

3-4 days ago update of ubuntu required restart of Ubuntu (linux kernel was updated).

After 3 days (i.e. yesterday) I restarted the system. I found that flashlib in Chrome became to work unstable, some artefact appeared, and only scrolling down-up in browser allowed to update view of screen. I run update manager. It showed ~88Mb of updates for last 3 days. 

After download of updates, apply changes was failed! I faced this first time (!). I remember message like "can not synchronize file /usr/share/..." or something like that.

I restarted ubuntu again. Now I could not login. System hangs after login. No Gnome menu appears etc. 

I tried to fix issue using dpkg. I found that some lib (ure) related to OpenOffice was not assigned (version XXX required, but bersion XXXY found). dpkg offered to solve this by some combination. I did so. Then I run dpkg update, and no errors appeared.

Also I updated VirtualBox to version 3.2.4, updated VirualBox Additions via console terminal in ubuntu. 

But still I can't fix problem with gdm/gnome.

dpkg-reconfigure gnome-*** did not help for me.

I tried to check logs, but I have not found something "interesting".

Could you please give me a hint how to fix it? 

At the moment terminal is the only way to login.


Thanks in advance. Ivan.

---

### Post by Peter09 on 2010-06-10
I wonder if you have a hard disk problem, or perhaps a full partition. Can you get into recovery mode and check your mount points?

---

### Post by vanchope on 2010-06-10
Thanks for the answer! Really, I think I had some problems with NTFS system. because I remember I could not delete some file in Windows 7, but after restarting file is deleted.

How to get recovery mode?... I mean, no grub menu appears

---

### Post by vanchope on 2010-06-10
Strange...I played a bit with some parameters like in described at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2), but grub menu does not appear anyway...

At the moment /etc/default/grub file looks like following:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
...

---

### Post by vanchope on 2010-06-10
Well, I just forgot to run update-grub. So, I started recovery-mode. Then I run dpkg fix problem. It started to do some stuff. I guess some packages, which were not finished during "failed" update. I run it again, and now only 1 package has some problems. 

Low graphical mode worked. Then I rebooted in normal mode and login works now!

So, at the moment we can mean this topic as closed. Thanks! :popcorn:

---

