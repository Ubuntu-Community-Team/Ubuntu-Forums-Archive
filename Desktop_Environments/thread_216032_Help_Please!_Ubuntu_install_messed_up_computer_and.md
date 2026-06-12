---
title: "Help Please! Ubuntu install messed up computer and now I can't install Windows.  Help"
date: 2006-07-14
forum: Desktop Environments
---

### Post by luckylucky on 2006-07-14
Hi,

I've made the bite to install Ubuntu on my full HD, but after noticing things that I can't get to work properly (I've hacked in many things) I've decided to revert back to Windows on my drive, with Ubuntu as a VMware app.

Now trying to get back to Windows I can't get it to install at all!!!  Does this have something to do with grub?

Anyhow, I'd appreciate it if someone could point me in the right direction to fix this issue to revert back to Windows.  Thanks in advance.

BTW, I absolutely love Ubuntu, and will again venture into making it my primary OS some day, but now I need to get back to work, and unfortunately I've lost several days of work (& income) on all this.

Thanks for the help.

---

### Post by luckylucky on 2006-07-14
Some more info for you...

I keep getting GRUB loading, please wait...
Error 17

if the above means anything

BTW, I've gone into bios to make sure that CD/DVD boots, and is on the top of the list of bootable drives.   Just mentioning this before someone replies with this tip.

Thanks again.

---

### Post by luckylucky on 2006-07-14
And another thing...

I've formatted my HD back to some kind of windows acceptable format (fat32) so that it has something to work from.

---

### Post by grim1234 on 2006-07-14
Sounds like a problem with your windows cd. If you are certain you've selected boot from cd in the bios, then make sure the cd is bootable. (make sure you aren't missing the 'press any key to boot from cd' option on boot).

gl,

G.

---

### Post by luckylucky on 2006-07-14
In desperation I've tried to install Win 2K just to see what would happen and I've got the following message in the begining of the install:


*** STOP: 0x000000a5 (0x000000b, 0x8904ad08, 0xc0000034, 0x89050b14)
The ACPI BIOS in this system is not fully compliant with the ACPI specification.  Please read the README.TXT (((I don't know where this would be))) for possible workarounds.  You can also contact your system's manufacturer for an updated BIOS, or visit [http://www.hardware-update.com](http://www.hardware-update.com) to see if a new BIOS is available.

The BIOS in this system is not fully ACPI compliant.  Please contact your system vendor or visit [http://www.hardware-update.com](http://www.hardware-update.com) for an updated BIOS.  If you are unable to obtain an updated BIOS or the latest BIOS supplied by your vendor is not ACPI compliant, you can turn off ACPI mode during text mode setup.  To do this, simply press the F7 key when you are promted to install storage drivers.  The system will not notify you that the F7 key was pressed - it will silently disable ACPI and allow you to continue your installation.


Man, I feel way over my head.  If it is of any help here is the link to the suppliers' website about the computer I have:
[http://support.gateway.com/s/Mobile/Q106/BladeC/1008963nv.shtml](http://support.gateway.com/s/Mobile/Q106/BladeC/1008963nv.shtml)

I am soooo grateful to anyone who can help on this matter.  Thanks.

---

### Post by luckylucky on 2006-07-14
Thanks grim, I did get that.  That's why I tried with another Windows CD (2K) and did catch the "press any key" for CD boot.  But then I get that ACPI bios thing.  I'll try with Win ME CD, but kind of suspect the same thing.

> **grim1234 said:**
> Sounds like a problem with your windows cd. If you are certain you've selected boot from cd in the bios, then make sure the cd is bootable. (make sure you aren't missing the 'press any key to boot from cd' option on boot).

gl,

G.

---

### Post by gerkin on 2006-07-14
Sorry to hear you are having so much trouble, getting windows to install is often a problem (the older versions anyway).

A couple of hints: you should always make a backup CD of the important stuff before you start (especially anything involving re-partitioning).  

From your original post it sounds like a minor Grub fix would have got things running but we are probably past that point now.  Also if things don't go to plan STOP and ask for help otherwise you'll start compounding errors.

I don't mean to preach and I'm keen to help so a few questions...

have you changed any of your bios settings, if so what?

Can you remember what you changed, so you can change it back? (don't make guesses though)

will the Ubuntu CD boot? (the live CD version should), if so we can probably use that to put things back how they should be.  Alternativly if you don't have the "live"  otherwise you could download it of any live distro CD like Ubuntu, Puppy, Knoppix, Mepis etc.

It will almost certainly be easier to get a linux distro running than windows in my experience, (my last Window98 install took about 5-6 attempts)

can you give more detail on your steps up to this point?

---

### Post by TheBlackNoodle on 2006-07-14
Can you try turning off power management in your BIOS? Seems like Windows just doesn't agree with your settings. Maybe power management for the CD Drive is turned on and it doesn't know how to manage it.

---

### Post by Herman on 2006-07-14
You really could have almost any problem with your computer and it could be completely co-incidental that you noticed problems showing up after trying to re-install Windows. 
Quite possibly the same problems were the reason why you couldn't get Ubuntu working properly all along.
You could try downloading the latest BIOS update from your computer's motherboard manufacturer and flashing your BIOS with it to see if that helps.
There is a little battery on your motherboard like a watch battery that runs out of power eventully and needs to be replaced, maybe that's your problem. 
It also could be something wrong with your power supply of almost anything, but begin trying the simplest and cheapest problem first and work towards the more complex and costly solutions later.
You might be able to see something wrong by going into 'System Health Check' or the equivalent in your BIOS and watching your readings there. 
I wish you good luck with your problem , but please don't blame Ubuntu or GRUB unless you are sure it is something to do with the software. I think it will turn out to be some other problem completely.
If I can think of anything more helpful I'll let you know. 
Regards, Herman :D

---

### Post by slider on 2006-07-14
[http://support.microsoft.com/default.aspx?scid=kb;en-us;Q256841](http://support.microsoft.com/default.aspx?scid=kb;en-us;Q256841)

---

### Post by luckylucky on 2006-07-15
First of all, thanks to everyone who has been kind enough to respond with some help tips.  This post is to reply to some of the points a few of you have pointed out.

In reply to someone else's post, I want to be very clear here that I don't blame Ubuntu/GRUB... in fact I'm a big time advocate of it, having hooked other people on it too.  I absolutely love Ubuntu and will totally continue using it, however as a VMware app (maximized to appear as though it is the actual OS).  I will again try to convert back to Ubuntu as the main OS.

Yes, Ubuntu does load, and I'm doing a new install of it as we speak.  I'm going to stick it out for now with Ubuntu on this machine, since it's the path of least resistance for now.  I need to get work done.  The stuff that was needed on a Win XP machine, well, I'm just going to do it on another machine.

FYI, this isn't the first time I ran into this whole mess.  Last year I installed Ubuntu (5.10) on another laptop (dual boot), decided to revert back to 100% Windows and came across the exact same senario.  I finally shipped the computer back to the manufacturer and a month later I got it back in original condition.  

Based on someone's comments, this is a brand new computer, about 2 months old, so I know that it isn't a battery issue.  Furthermore, the other computer (an Averatec) that I mention in the above paragraph was only about 6 months old at that point.  Same problem.  Thus same problem on 2 different computers.

Since someone asked (assuming I buggered up something ) in BIOS I only went there AFTER this problem has presented itself.  I just changed the order of booting drives, putting the CD/DVD on the top of the list.  Much later, in an act of desperation after numerous failed attempts to get XP, 2000 or ME to install, I went in and clicked on restore defaults (after looking around it doesn't appear to have done any changes).  From my research it appears that by having installed Ubuntu it added GRUB, which replaced the default equivalent.

I'm absolutely certain that it isn't that I've done something wrong.  In fact I'm sure that others must have the same experience (go ahead, buy a NEW laptop computer, install Ubuntu, then try to re-install Windows from CD).  Unfortunately I've learned from the experiences to be warry of installing linux on a machine that I might want to revert back to Windows.

Well, for now anyhow, I'm going to keep Ubuntu on this computer.  I don't have the time to be messing around with the computer to restore windows.  I have work to do (you know like to pay bills).

I am hoping to see if anyone else has encountered the same situation, and also how to fix it.  I'll be looking in this thread hoping to find an answer so that I can then possibly implement it too.

Thanks to everyone!

---

### Post by luckylucky on 2006-07-15
I realize that this thread has taken on a rather negative tone, but please know that I think that Ubuntu is fantastic (it's my overall favorite linux, and I've tried several).

On a positive note, I've learned a tremendous amount about linux, especially how to work in terminal, this past week.  In the end I think that this whole experience will result in me growing into a linux power user... something I kind of wished for many years (to be a linux pro).

Ubuntu rocks!

---

### Post by vampiric_blade on 2006-07-15
You need to get grub off of your mbr as windows will not replace what it needs in the mbr via installation.  A simpe fdisk /mbr from a windows bootdisc/cd will solve that.   Then, assumming you can properly boot from your cd, you should be o.k.

---

### Post by Herman on 2006-07-15
I apologize if my post came across as having a negative tone, I didn't know until now if you had a new or old computer and I have never had any problems myself installing Ubuntu , then Windows. 
I have had some experience with old computers myself, and all kinds of problems like old batteries, old BIOSes that needed flashing, etc, etc, so I was offering the best advice I knew from my own experiences. Looks like you took me a bit wrong too. Once again, I'm sorry.
Was slider's post under mine any help? I thought that one would have solved it.
Anyway, we're all on your side, and I'll try to make sure I watch the mood of my posts more in future :D
Regards, Herman

---

### Post by Moyerman on 2006-07-16
I think I have the exact problem you have. When you try to boot C: does "GRUB" load and give you error 17? When you run FDISK in DOS is there a extended partition you can't delete? I think we both have master boot record issues. I'm trying to find out if I should try to delete the MBR or reinstall Linux and try FDISK from there. I have the two disk set and I can boot the "LIVE CD" Any ideas?

---

### Post by kufford on 2006-07-16
It sounds like your computer needs to be completely formatted. Try downloading a rescue disk and completely erasing all partition schemes that are on your machine. Then, reinstall windows...

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

That should fix it... Seems like the MBR is screwed up, although I'm not sure why the windows disk won't boot...

---

### Post by luckylucky on 2006-07-16
Hi everyone,

Thanks for all of your assistance in this thread.  I am greatful to all of you for your help.

What you should know is that I'm a self-proclaimed idiot.  After digging around I found that my computer did actually come with a Windows recorvery disk, and that the disk that I was attempting to boot from was infact the supplimental software recovery disk... hence why it wasn't bootable (improperly labled by me).

I feel like a total nincompoop.  

Please disregard this thread, and perhaps a moderator could completely delete it.  Sorry for all the chaos I've created and I hope that all will forgive me.

I am using Ubuntu within VMware and it is my primary working platform.  I love Ubuntu and am looking forward to the future with it.

Best wishes to all!

LuckyLucky

---

### Post by hi_mostafa on 2007-11-21
I know this is an old post , but i was using Windows boot-loader with grub installed on ext3 partition  and Windows bootloader points to a 512 bytes of bootimage of ext3 partition (done with dd command )

and now i am talking from ubuntu live cd w, after removing both ubuntu and windows xp ..

I am facing the same problem and i don't know what to do .

---

### Post by hi_mostafa on 2007-11-21
I am having a Gigabyte 8IR-2003 Motherboard , and I had already installed Windows xp FROM SAME cd several times with no such ACPI Error .

---

