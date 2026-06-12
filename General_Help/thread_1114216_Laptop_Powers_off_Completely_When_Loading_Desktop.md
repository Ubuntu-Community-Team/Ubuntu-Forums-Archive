---
title: "Laptop Powers off Completely When Loading Desktop"
date: 2009-04-02
forum: General Help
---

### Post by TwoTime on 2009-04-02
**_Issue:  _**
Laptop turns itself completely off (no power) during the loading of the desktop.  As soon as I hit the “power on” it goes through the BIOS diagnostic screen, then the Ubuntu progress bar, and lastly it gets to the splash screen and turns the laptop off.  It can be turned back on directly after and experience the same routine.  This failure will occur 9 out of 10 times, however, 1 out of 10 times it will completely load and the OS will work without a problem. (Estimated #’s)

**_Laptop Info:_**- IBM/Lenovo Thinkpad A31 - IBM R40
- Intel Mobile Pentium M at 2.0GHz
- 768 MB RAM
- Currently running the entire Ubuntu OS solely off of a Toshiba USB external hard drive.
- The laptop has been stripped of all the unnecessary parts (i.e. CD-ROM, wifi cards, battery, laptop hard drive, etc) – Problem still occurred while laptop was still assembled.

**_Other Important Info:_**- I have transferred the external hard drive to another laptop and have ran Ubuntu for hours with no problem
- I don’t believe that it is an overheating issue due to the fact that I can leave the laptop running for hours while Ubuntu checks the disk for errors or when I am in a boot menu between projected solutions.  The fan runs without any problems.

**_Diagnosis - Failed Attempts to Fix_**:
- I have extensively cleaned the heat sink as well as the CPU fan.  This is not clogged.
- I have reapplied thermal paste on the CPU.
- Memory test – RAM modules have past BIOS diagnostic setup as well as the Memory86+. 
- Boot Options – Tried altering the Kernel boot line by turning off the acpi. (noacpi, and acpi=off) both did nothing. 

**_Solutions – Ideas:_**
- ???????

Sorry about the long post but I really want to fix this irritating problem, and it seems that posts always ask for more information, so I am trying to provide everything I know right from the beginning.  Please help.  I will be more then happy to entertain any questions.

---

### Post by 3Miro on 2009-04-02
Giving a lot of information is great and don't worry, people will always ask for more information :)

My thinking is that it might be driver related. If you are running Ubuntu on another computer and then moving the HD to your laptop, hardware is different and thus different drivers have to be loaded. It is just a hypothesis and I am knowledgeable enough to tell you how to test it.

I can of trying the LiveCD to see if that always boots normally. Also did you try booting in save-mode, if it is driver related that might help.

Another think that comes to my mind (since it seems that you are reaching the desktop), next time you manage to log in, go to 
```
System -> Admin -> Sessions
```
and turn everything off. If the problem disappears, stat turning stuff back on to see which service was the evil one.

---

### Post by TwoTime on 2009-04-03
Thanks 3Miro for the input.  I too believe that this is driver related, but fixing it sounds like it is going to be painstaking. 

When I start in recovery mode I can get all the way to the recovery menu.  Then faced with the decision to boot normally or not.  Do you suggest that I do anything different?

Once I reach the desktop I will try the code and shut everything off as you suggested.  I will let you know what I find out.

---

### Post by TwoTime on 2009-04-08
So I finally booted into the desktop and had the opportunity to play around.  I shut everything off in the system -> preferences -> sessions.  I did try a few things before restarting, and when I tried open a folder that was full of pictures the system shut off.  I tried to turn it back on and it seems that turning off everything in sessions didn't do the trick, the system shut off. 

I did fail to say that before I get the the desktop I get a screen that is filled with black and white bars.  With saying that and having a hard time loading picture thumbnails could this be a video driver related problem?

---

### Post by macjones on 2009-04-25
Exact same bug here, laptop is a Toshiba m35x.

Bug found when upgrading from 7.04 to 9.04, 7.04 works fine.

9.04 has all the issues in this bug and does boot properly 1 time out of 10 as well.

Mac

---

### Post by macjones on 2009-04-25
Got it working.

Fix : Upgrade Laptop Bios

How: go to toshiba.com and download the latest version bios for your model.

My bios was at v1.20 >> now at v2.00 (hit F2 on boot to see version)

Download the exe file from toshiba - you do not need to be in MS Windows - safer that way too :-)

Open the exe in ubuntu and extract the ISO image. (1.8mb)

Right click on the iso and burn it to CD.

Boot the laptop off that CD and it will upgrade your bios.

My M35X Toshiba Satellite system is now 100% working.

Mac

To determine VGA type (ati or intel) boot into recovery mode and do:

lspci | grep VGA

The bios update is graphics board specific.

---

### Post by TwoTime on 2009-04-26
Mac, I am going to give this a try.  I hope that this does the trick for me too.

---

### Post by TwoTime on 2009-05-03
Well, updated the system BIOS to the most recent version.  Then I updated to 9.04 thinking that the bug may have been fixed there too.  However to my dismay I still have the same problem.

---

### Post by TwoTime on 2009-05-26
As an update...I took my external hard drive off and booted into it with another laptop.  I went to the update manager downloaded and installated the lastest updates.  I hooked it back onto the IBM A31 and booted into it.  It did the exact same thing that it always has done.  Turns off right before the desktop loads. 

However for S&G I loaded the other kernal in the GRUB menu upon start up and the full desktop loaded.  Thinking every blind squirel finds a nut, I booted into the desktop numerous times with no problems whats so ever.  

I thought that the old kernal was there in case your "recent update" doesn't go as planned... not the other way around.  Isn't the kernal that I using considered to be the "old" version (lower numeric code) and the new one would be the updated one (higher numeric code)?  This means I am booting into what didn't work previously right?  

I guess I got it to work and should ask questions but seems strange.  Maybe I should considering never updating ever again.

---

