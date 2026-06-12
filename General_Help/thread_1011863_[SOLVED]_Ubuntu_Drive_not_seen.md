---
title: "[SOLVED] Ubuntu Drive not seen"
date: 2008-12-15
forum: General Help
---

### Post by chaplanger on 2008-12-15
I have two hard drives on my system:
Drive #1 -- Windows XP is installed
Drive #2 -- Ubuntu 8.04

PROBLEM: 
After accidentally wiping out my original Windows installation on Drive #1, I reinstalled windows on it.  To make certain that nothing happened to my #2 drive, I disconnected it from the system.

After reconnecting the Ubuntu Drive (Drive #2) my system does not find it to boot into.  I believe this is more than simply needing to adjust the MBR. Not only can I not boot to my Ubuntu partition, the drive (Drive #2) is no longer recognized.

WHAT I HAVE TRIED:
I have disconnected the Windows Drive (Drive #1) making the Ubuntu drive the only one active on the system.  The drive is not recognized as a bootable drive at all.  

I can access the drive using a Live CD start and then finding the drive this way.  However unless I then proceed to enter into this installation via a 'root' route -- I cannot do anything with the installation.

WHAT I NEED:
How do I make this drive bootable once again?  What steps do I need to take?

Be aware that in many ways I am still a Ubuntu (Linux) Novice (having been away from it for over a year because of military deployment).  So when advice is given, assume that I remember very little and please give a step-by-step (hand-holding) instructional.

Thank you.

---

### Post by taurus on 2008-12-15
Connect both drives.  Then, use your LiveCD to reinstall GRUB to MRB.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ajgreeny on 2008-12-15
I suspect you do simply need to reinstall grub using the Ubuntu live CD.  The fact that the live CD can see the ububntu install bodes well, so don't worry too much.  Simply do as follows:-

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by chaplanger on 2008-12-15
First of all, thank you for your encouragement and advice -- I attempted to do what you requested through the terminal -- here is what I received in return:


grub> find /boot/grub/stage1
 (hd1,0)

grub> setup (hd1)

Error 12: Invalid device requested

grub> setup (hd0)

Error 12: Invalid device requested

grub> 

--------------------------
Since I was given (hd1,0) as the parameters I attempted the setup through hd1.  As you can see, this was rejected.  I then tried the default (hd0) and that also returned the error message.

How do I get beyond this?

---

### Post by chaplanger on 2008-12-15
RESOLVED:
I realized that I did not set the root parameter as mentioned above -- once this was completed all else worked flawlessly.

Once again thank you so much.

The Ubuntu community is top notch when it comes to providing real help!

Blessings to all in this Christmas season.

---

### Post by ajgreeny on 2008-12-15
Great!  Glad it worked for you.

---

