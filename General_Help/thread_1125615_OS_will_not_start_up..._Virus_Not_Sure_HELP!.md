---
title: "OS will not start up... Virus? Not Sure HELP!"
date: 2009-04-14
forum: General Help
---

### Post by craigerts on 2009-04-14
My son has a dell laptop... one of the small inspirons... it has the ubuntu os on it... he was surfing on a social networking site the other day and a pop up ads attacks him saying he has a virus that he needs to clear... well that was all she wrote... I cant get the thing to respond - the dell symbol come up ubuntu appears to load - then the screen goes white... 

There's no disk drive so I cannot use the CD - I tried to load the CD onto a jump drive but it's to big... My kid is really bummed out 

Can you guys help get this machine working again - I would really appreciate it- thanks

---

### Post by pytheas22 on 2009-04-14
If a virus rendered your son's Ubuntu system unbootable, it would be the first case in the world of malware taking down a Linux system "in the wild."  A much likelier explanation is that some configuration error is causing the system not to boot for some reason.

Please answer a few questions so we can get a better handle on what might be wrong:

1. how far does the system boot before the screen goes white?  Do you see the orange Ubuntu bar?
2. if you press control-alt-F1 while the system is booting, you should see a textual display showing you what the computer is doing at each point in the boot process.  Do you see any error messages?  What is the last line displayed before the screen goes white?
3. if you press control-alt-backspace at the white screen, what happens?
4. if you press control-alt-F2 at the white screen, what happens?
5. if you press the capslock or numlock keys at the white screen, do the corresponding LEDs light up on the keyboard?

Also, if it helps, you can install Ubuntu to a USB stick and boot to it on your son's computer (and optionally use it to reinstall the system, which might be the easiest solution to your situation depending on whether your son has a lot invested in the non-booting system).  The easiest way to create a bootable USB drive is to find a computer running Ubuntu and go to System>Administration>Create a USB startup disk.  If you don't have Ubuntu installed on any other computers, you should still be able to create the startup disk while running off the Ubuntu live CD.  There are also ways to create a bootable Ubuntu USB drive from Windows, but they're more complicated (if you are interested, however, I'll find you the links).

---

### Post by 3Miro on 2009-04-14
During boot, there should be a counter that counts for 2 - 3 seconds. If at that time you press escape (I believe it was), you should be able to get into the Grub menu and select to boot in "recovery mode".

If a setting file has gone bad (which is probably what happened, I mean hitting Linux just from opening a we-page is unheard of), then you should be able to fix it from there.

You can also use the recovery mode to backup files in case a full reinstall is needed.

---

### Post by InspirationDate on 2009-04-14
Yeah, I just installed a bunch of updates and now my computer won't boot.  Probably the same sort of thing.

---

### Post by 3Miro on 2009-04-14
> **InspirationDate said:**
> Yeah, I just installed a bunch of updates and now my computer won't boot.  Probably the same sort of thing.

If you are using Gutsy Gibbon, then you should update your system (or profile).

The problem above wasn't created by updates, but unsafe reboot. You should probably start a new tread and describe your specific problem so people don't get mixed up on which tread refers to which problem.

---

### Post by InspirationDate on 2009-04-14
Sorry, wasn't asking for help.  Just wanted to support the fact that it isn't a virus that is the problem.  I shouldn't have said anything I guess.

---

### Post by 3Miro on 2009-04-14
> **InspirationDate said:**
> Sorry, wasn't asking for help.  Just wanted to support the fact that it isn't a virus that is the problem.  I shouldn't have said anything I guess.

Sorry I misunderstood you. Of course you can and should make a valid comment.

I am just waiting for craigerts to say what he has tried and what worked/did not work.

---

### Post by craigerts on 2009-04-14
Thank you for your help so far - here are the answers to your questions


1. how far does the system boot before the screen goes white? Do you see the orange Ubuntu bar?

**- yes I do see the orange ubuntu bar the screen flickers after that and goes white**


2. if you press control-alt-F1 while the system is booting, you should see a textual display showing you what the computer is doing at each point in the boot process. Do you see any error messages? What is the last line displayed before the screen goes white?
**it wont load at all when I do this - it stays at MBR 2FA**


3. if you press control-alt-backspace at the white screen, what happens?
**- It takes me to a log in page... I log in and it goes back to white **


4. if you press control-alt-F2 at the white screen, what happens?
**nothing happens at all.**



5. if you press the capslock or numlock keys at the white screen, do the corresponding LEDs light up on the keyboard?
there are no led's for these

---

### Post by craigerts on 2009-04-14
Okay I do have another ubuntu system here - but I do not see that I can create a start up disk from that... I followed the directions you gave me - and nothing was there for me to do that. 

I do have a ubuntu live disk... can I put that in my windows XP and load it onto a jump drive? I was not successful at doing that last night

thank you again for your help

---

### Post by craigerts on 2009-04-14
The system is Ubuntu 8.04

---

### Post by codeseer on 2009-04-14
> **craigerts said:**
> Okay I do have another ubuntu system here - but I do not see that I can create a start up disk from that... I followed the directions you gave me - and nothing was there for me to do that. 

I do have a ubuntu live disk... can I put that in my windows XP and load it onto a jump drive? I was not successful at doing that last night

thank you again for your help

You can create a USB startup disk by going to System->Administration->Create a USB Startup Disk

---

### Post by dmizer on 2009-04-14
> **craigerts said:**
> Okay I do have another ubuntu system here - but I do not see that I can create a start up disk from that... I followed the directions you gave me - and nothing was there for me to do that. 

I do have a ubuntu live disk... can I put that in my windows XP and load it onto a jump drive? I was not successful at doing that last night

thank you again for your help

You'll need a live CD of 8.10 (ibex): [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Then you can boot to the live cd (on your Windows computer) and create a bootable USB drive according to the directions that [codeseer gave above](http://ubuntuforums.org/showpost.php?p=7074186&postcount=11). You'll need a USB drive with at least 1gig of space.

---

### Post by pytheas22 on 2009-04-15
> 3. if you press control-alt-backspace at the white screen, what happens?
- It takes me to a log in page... I log in and it goes back to white 

That makes me suspect that the issue lies with your graphics driver and/or X11 configuration (which is good, since it means the system itself is probably still in good shape).  When you press control-alt-backspace and return to the login screen, click the options menu (I believe it's in the lower-left corner) and select a 'Failsafe Gnome' session.  Then enter your username and password and log in.  Does this work?
> 
Okay I do have another ubuntu system here - but I do not see that I can create a start up disk from that... I followed the directions you gave me - and nothing was there for me to do that.

I do have a ubuntu live disk... can I put that in my windows XP and load it onto a jump drive? I was not successful at doing that last night

Unfortunately it's not as simple as merely copying the live CD onto the USB drive.  You need also to make the drive bootable, etc.  The 'Startup disk creator' will take care of this for you automatically.

The reason you don't see an option to create a USB disk under System>Administration is that you're using Ubuntu 8.04.  The USB creator was only included by default in Ubuntu 8.10 and later.  However, you can still easily install the USB creator via the links on [this page]("http://ubuntuliving.blogspot.com/2008/11/usb-creator-for-hardy.html").  (I'm not positive, but I think you could also install it if you enabled the 'hardy-backports' repository from System>Administration>Software Sources, and then typed 'sudo apt-get update; sudo apt-get install usb-creator'.)

Alternatively, just boot to an Ubuntu 8.10 live CD and create the startup disk there, as outlined in the posts above.

---

