---
title: "How do I factory restore 7.04 to Inspiron 1420"
date: 2007-10-25
forum: Dell  Ubuntu Support
---

### Post by RobertGloverJr on 2007-10-25
I bought a new 1420, which arrived three days ago. Last night I upgraded a non-Dell laptop from Ubuntu 7.04 to Ubuntu 7.10 and it went perfectly, so I then tried to upgrade the Dell 1420 to 7.10.
 
  My new 1420 is now a brick.

  Fortunately I learned by googling that I can restore the 1420 to it's factory condition (i.e., Ubuntu 7.04) by using GRUB.

    The problem is that I cannot figure out how to make  GRUB appear so that I can select the "restore from factory default option".

   When I turn the power on the system hangs after printing a screen of Linux information on a black screen in text mode.

  So my guess is that I have to hit a control key of some sort immediately after turning the power on.

  Suggestions very much appreciated on how to restore my new Dell 1420 to factory condition, i.e., Ubuntu 7.04

---

### Post by RobertGloverJr on 2007-10-25
Incidentally, I received this error message during the (failed) upgrade to 7.10:

"unable to mount the volume 'OS'.
mount: wrong fs type, bad option, bad superblock on /dev/sda2 missing codepage or helper program, or other error.  In some cases useful info is found in syslog  - try dmesg / tail or so"

Another "interesting" thing that happens is when I power off/on it asks for the user to use for the Dell login.  Of course I have no idea what to enter for that.

---

### Post by notwen on 2007-10-25
> **RobertGloverJr said:**
> Incidentally, I received this error message during the (failed) upgrade to 7.10:

"unable to mount the volume 'OS'.
mount: wrong fs type, bad option, bad superblock on /dev/sda2 missing codepage or helper program, or other error.  In some cases useful info is found in syslog  - try dmesg / tail or so"

Another "interesting" thing that happens is when I power off/on it asks for the user to use for the Dell login.  Of course I have no idea what to enter for that.

How did you go about updating your Dell 1420n to Gutsy?  Through update manager or did you upgrade by installing Gutsy from CD?

---

### Post by RobertGloverJr on 2007-10-25
I did the upgrade through the upgrade manager.   First it asked me to apply all the updates to 7.04.  I gave it permission and that ran perfectly.  Then a new option appeared which offered me the option to update to 7.10.  I took that option and went to bed.  When I work up the following message was on the laptop: 

"Replace the customized configuration file /etc/kernel/postinst.d/dkms "

I answered "yes" to that question.

Then another question appeared on the laptop:

It asked permission to replace /etc/default/linux-restricted-modules-common

I gave it permission

Then I got an error message that said:

"Starting Common Unit Printing System:  cupsd  bad exit status:  0 ...
running local boot scripts /etc/rdc.local 

no resume image, doing normal boot

then it asks for the dell login password.  

Basically at that point the laptop is a brick as far as I'm concerned.
   

   I have not installed any softwared.  This laptop is exactly as it was when I got it out of the box three days ago.

   If somebody can give me instructions on how to use GRUB to restore it to the factory settings (i.e, 7.04)  I will be very happy.  I have no idea how to make the GRUB screen appear.  When I turn on the power it directly starts trying to boot up 7.10.

---

### Post by ebe326 on 2007-10-25
I think if you hit escape it should show up. It is just set to hidden mode. I don't know how to restore though. I also have a 1420N. I tried the update and it made it through but it wasn't right. I re-installed from the Dell remaster cd and tried the upgrade again and this time it was even worse. Finally I just did a fresh install of Gutsy and everything is working now. Of course, it might just be luck that I had no problems with the fresh install. Seems other people are still having some issues.

david

---

### Post by RobertGloverJr on 2007-10-25
> **ebe326 said:**
> I think if you hit escape it should show up. It is just set to hidden mode.

  I'll give that a try when I get home tonight.  I think the "restore to factory settings" will appears as one of the option on the GRUB menu.

   It's really bizarre that DELL shipped this new laptop to me with a manual that assumes the operating system is Window. Other than the CD containing Ubuntu 7.04 there is not one word anywhere on any of the material that came with the laptop that even mentiones the word Linux or Ubuntu.

   At the very least you would think they could include a one page piece of paper explaining how to re-set the laptop to the factory settings. 

   By the way, how did you manage to boot from that CD?  Did you have to press f2 or f12 to get into the BIOS and tell it to boot from the CD instead of the harddrive?

---

### Post by ebe326 on 2007-10-25
I think it was already setup to boot from cd before looking at the hard drive. Even if yours isn't, just look through the bios and change the boot order. BTW, I set the partitioning up like Dell did. I set /boot on sda3 and / on sda6. [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions)

david

---

### Post by notwen on 2007-10-25
> I'll give that a try when I get home tonight. I think the "restore to factory settings" will appears as one of the option on the GRUB menu.

This is accurate.  More info can be found [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation") at the [Dell Linux wiki]("http://linux.dell.com/wiki/index.php/Wiki_Main_Page").  You may wish to wait until Dell creates custom Gutsy images that include all of the hardware drivers in the 1420n as they did for Feisty.  Keep checking their Gutsy page [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").

---

### Post by RobertGloverJr on 2007-10-25
> **notwen said:**
> This is accurate

   Thank you for the additional links, they are very helpful.  I do wish to also ask for confirmation  however (because I can't try it until I get home tonight from work) that the way to make the GRUB menu appear is to turn on the laptop and then immediately press the ESC key.   Is that really all there is to it?

> **notwen said:**
> You may wish to wait until Dell creates custom Gutsy images that include all of the hardware drivers in the 1420n as they did for Feisty.  Keep checking their Gutsy page 

   I sure will!  One question I do have however, which is a little off topic, is the following.   Last night on  my  (non-dell ) desktop computer I installed ubunto 7.04 and then upgraded it to ubunto 7.10.  Then I installed VMWARE Workstation for Linux onto Gutsy.  The installation was easy and perfect.  I did not define a guest operating system but I did confirm that there were no error messages during the install of VMWARE and that I could start up the VMWARE utility.

   VMWARE says in the user guide that it supports ubuntu 7.04.  But VMWARE on their list of supported guest operating systems does not list ubuntu 7.10.  That is certainly reasonable since 7.10 came out on October 18.  I'm getting too off topic here, so let me close by asking if anyone has experience using WMWARE on a dell 1420 laptop under ubuntu.

---

### Post by notwen on 2007-10-25
> **RobertGloverJr said:**
> Thank you for the additional links, they are very helpful.  I do wish to also ask for confirmation  however (because I can't try it until I get home tonight from work) that the way to make the GRUB menu appear is to turn on the laptop and then immediately press the ESC key.   Is that really all there is to it?



   I sure will!  One question I do have however, which is a little off topic, is the following.   Last night on  my  (non-dell ) desktop computer I installed ubunto 7.04 and then upgraded it to ubunto 7.10.  Then I installed VMWARE Workstation for Linux onto Gutsy.  The installation was easy and perfect.  I did not define a guest operating system but I did confirm that there were no error messages during the install of VMWARE and that I could start up the VMWARE utility.

   VMWARE says in the user guide that it supports ubuntu 7.04.  But VMWARE on their list of supported guest operating systems does not list ubuntu 7.10.  That is certainly reasonable since 7.10 came out on October 18.  I'm getting too off topic here, so let me close by asking if anyone has experience using WMWARE on a dell 1420 laptop under ubuntu.

Yes, you can access the GRUB menu by hitting escape during the loading phase.  You should have a 3-5 second gap to press ESC before GRUB proceeds to boot Ubuntu.  Once you're in the GRUB menu simply select the last option 'Reinstall Operating System'.  Good luck and hope this helps. =]

---

### Post by joker2of5 on 2007-10-25
I too just purchased a Dell 1420n with ubuntu fiesty fawn 7.04 pre installed.  I have had mine a bit longer though and have saved some things to the hard drive I would not like to loose.

Last night I upgraded to 7.10 Gutsy Gibbon and the process was very similar to the one described above.

when I get the login screen I log in with my user name and password.  Then I type "startx" hoping it will start the graphical desktop

The error message I get says: 
(WW) I810: No matching Device section for instance (BusID PCI:02:1) found 
(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
         after 0 requests (0 known processed ) with 0 events remaining.

I did try pressing escape during the boot up process and I got a menu with the option to restore the operating system.  I have not tried this yet because it says it will delete my hard drive and I do have some files that I would rather not delete

---

### Post by joker2of5 on 2007-10-25
I found this fix on another thread on this same forum

type
sudo dpkg-reconfigure xserver-xorg


accept the defaults

It seems to be working now

---

### Post by actuary09 on 2007-10-25
Call up dell technical support.  They can restore factory defaults -- probably ubuntu 7.04

---

### Post by deserthowler on 2007-10-27
> **ebe326 said:**
> I think if you hit escape it should show up. It is just set to hidden mode.

A real quick tapping of F12 at boot should put you into the Dell menu which has a reinstall option if I remember correctly.  F2 will put you into the BIOS.  

I reset my BIOS from quick boot because it gives me time to react.  I also set the time for grub to 10 seconds before it auto boots.  I can spare the time. I probably waste 5 to 10 minutes a month doing this though. :lolflag:

Earl

---

### Post by RobertGloverJr on 2007-10-27
I was able to to a flawless, perfect reinstallation to factory settings by pressing ESC right after powering up. That made the GRUB menu appear, and the last entry was the one to restore from factory settings.  Fifteen minutes later everything was exactly the way it was when I first turned it on after taking it out of the box.
  Thanks for everyone's help on this.

---

