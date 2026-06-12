---
title: "GRUB error"
date: 2011-01-10
forum: Desktop Environments
---

### Post by vchapman on 2011-01-10
I have a dual boot Win XP / Ubuntu 10.10 system. Everytime I boot into Ubuntu, I get an error that begins VGA=791 Deprecated followed by some other information that tries to be helpful. When the message eventually gets replaced, I get the Ubuntu 10.10 splash screen followed by a screen that is out of sync. Then I get my desktop.

Prior to the VGA=791 message, I think that I get a couple of error messages, They go by too fast to be read.

How do I edit the grub startup stuff to fix all of this?

---

### Post by oldfred on 2011-01-10
If you upgraded from grub legacy to grub2 it copied parameters from the old grub menu.lst into  /etc/default/grub. You need to delete the VGA= from the grub file and uupdate grub.

gksudo gedit /etc/default/grub
sudo update-grub

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by vchapman on 2011-01-19
> **oldfred said:**
> If you upgraded from grub legacy to grub2 it copied parameters from the old grub menu.lst into  /etc/default/grub. You need to delete the VGA= from the grub file and uupdate grub.

gksudo gedit /etc/default/grub
sudo update-grub

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Well I did all of this a week or more ago. Unfortunately, I seemed to have create a greater problem.

There is now a problem with the graphics so the system no longer starts. I can run it in safe mode and enter 'startx' from the command line. This works somewhat, but I can't get the network to start. So I am not sure where to go from here.

I am keying this from Windoze so this is from memory. I did have a problem with the nvidia driver when I went Ubuntu 10.10. I then went to the generic driver. It worked OK until I fixed the grub problem. If the nvidia-96 problem has been fixed, I can't download it as I can't get the network to run. So....

---

### Post by oldfred on 2011-01-19
You may want a new thread on the networking issues, so those with network knowledge may help. I know just enough to search in the forum or google for what few network issues I have had, and none recently.

Have you tried nomodeset on the grub command line?

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by vchapman on 2011-01-20
Well after a couple of hours of fiddling around I got my system back to the state where I started this thread. I then applied the suggestions in post #2. So that problem is now fixed. Thank you.

I still have issues with nvidia and how to make it work, but that is for a new posting.

---

### Post by vchapman on 2011-01-20
Well after a couple of hours of fiddling around I got my system back to the state where I started this thread. I then applied the suggestions in post #2. So that problem is now fixed. Thank you.

I still have issues with nvidia and how to make it work, but that is for a new posting.

---

### Post by vchapman on 2011-01-20
Well after a couple of hours of fiddling around I got my system back to the state where I started this thread. I then applied the suggestions in post #2. So that problem is now fixed. Thank you.

I still have issues with nvidia and how to make it work, but that is for a new posting.

---

### Post by vchapman on 2011-01-20
Well after a couple of hours of fiddling around I got my system back to the state where I started this thread. I then applied the suggestions in post #2. So that problem is now fixed. Thank you.

I still have issues with nvidia and how to make it work, but that is for a new posting.

---

