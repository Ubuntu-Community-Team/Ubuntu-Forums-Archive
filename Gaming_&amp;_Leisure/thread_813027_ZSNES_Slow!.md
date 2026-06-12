---
title: "ZSNES: Slow!"
date: 2008-05-30
forum: Gaming &amp; Leisure
---

### Post by Twilight in Zero on 2008-05-30
Hello there! I'm trying to enjoy some games in ZSNES. I have two problems with it, but the biggest one is that it's very slow. I know you guys might not like the W word, but I have to compare here. I can run ZNES on Windows, using the HQ3x filter, and get 60 FPS. Using the SuperEagle filter on Ubuntu, I get around 30 FPS.

I have an ATI Radeon Xpress 1150, and I am using XGL and Compiz, but I'm running ZSNES with the nonXgl script in this thread: [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636) Before I did that, it was **unbearably** slow. I know my computer's capable of running it faster, though!

The other problem is that it won't load the save games I have on my FAT32 partition, in /media/drv0/Program Files/zsnes/Save. Any advice on what to do about either of those?

EDIT: Sound is really bad too. I can get it to run full speed by disabling the filter. But the sound is really bad... and I shouldn't **have** to disable the filter.

---

### Post by MaindotC on 2008-05-30
I'm so sorry you're having these problems. I run Z on my T60 and I've never had any problems, even if I ran it in XGL. I pretty much left everything at default and never had any problems, even full screen. Do you play on zbattle.net?

---

### Post by disturbedite on 2008-05-30
i was gonna say to try disabling the filter if you're running one but it looks like you might have figured that already.

---

### Post by acoustibop on 2008-05-30
As far as loading/saving to your FAT32 partition is concerned, Twilight in Zero, have you checked whether you have the appropriate permissions to read and write to the folder your saves are in?

There have been a large number of threads on sound in ZSNES recently; you really should search.  What version of ZSNES do you have installed and how did you install it?

---

### Post by Twilight in Zero on 2008-05-30
I don't play on zbattle.net... I've never heard of it until now. I'm just trying to play a re-retranslation of Chrono Trigger. I've beaten it, but there's still New Game +... :P

What the heck kind of computer do you have to where you can play a game even with xgl on for the same window? Am I doing something wrong, maybe?

---

### Post by acoustibop on 2008-05-30
A couple of things, Twilight in Zero - what driver are you using for your videocard?  For an ATI Radeon Xpress 1150, you really want to install the fglrx driver. Go to System -> Administration -> Hardware Drivers if you're using Hardy, or System -> Administration -> Restricted Drivers Manager if you're using Gutsy, and tick the box for the ATI Accelerated Graphics Driver.  Ubuntu will then download and install the fglrx driver and you'll need to reboot.

Also, try running the emulator with Compiz disabled.

---

### Post by Twilight in Zero on 2008-05-31
Hey, looks like you snuck a post in right before I posted my last one, and I didn't even notice it. Sorry about that, man. But that is a good point, a lot of the folders on my FAT32 partition are read-only (and I have no clue why... **I** didn't set them read-only). It's annoying to go back to Windows just to unset read-only. I wonder if I can't do it from Ubuntu. I'll google that.

I already have fglrx installed. I don't know if I mentioned that or not. But here it is now. I'll see what I can do about temporarily disabling compiz, and I'll see if it helps at all.

EDIT: Disabling Compiz didn't help my framerate, and I added write access to every folder on my FAT32 partition, but it still wouldn't load my saves.

---

### Post by acoustibop on 2008-05-31
Changing folder permissions on a FAT32 partition in Windows won't make any difference to how Linux sees them, Twilight in Zero.  You need to do it in Linux: see [here]("https://help.ubuntu.com/community/FilePermissions") for an explanation of the CHMOD command.

---

### Post by MaindotC on 2008-05-31
Chronotrigger - unbelievably awesome game.

---

### Post by Twilight in Zero on 2008-06-01
I already changed the file permissions. I said that in my last post. But giving all of my files write access didn't make any difference.

And yes, Chrono Trigger is unbelievably awesome. Even more so with the retranslation (The **re-**retranslation by Doctor L). But I want to enjoy it in Linux. I could always streamline my Windows install so that rebooting to it isn't so tedious, but...

---

### Post by acoustibop on 2008-06-01
Yes, but you said "It's annoying to go back to Windows just to unset read-only," Twilight in Zero which, as I said, won't work - except for your Windows installation.

You need to change the file permissions in Linux, and I gave you a link for the chmod command that you do that with.

How do other games work in ZSNES for you?

---

### Post by Twilight in Zero on 2008-06-02
> **acoustibop said:**
> Yes, but you said "It's annoying to go back to Windows just to unset read-only," Twilight in Zero which, as I said, won't work - except for your Windows installation.

You need to change the file permissions in Linux, and I gave you a link for the chmod command that you do that with.

How do other games work in ZSNES for you?

I guess I also didn't make it clear that I used chmod. I did use chmod and it worked. My bad.

Other games run badly as well.

---

### Post by acoustibop on 2008-06-03
Since you're using the fglrx driver, Twilight in Zero, can you do fglrxinfo in a terminal and post the results here, please?

---

### Post by Twilight in Zero on 2008-06-04
Okay, here you go. And you can call me TiZ if you want. Twilight in Zero is a lot to type.


display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

---

### Post by acoustibop on 2008-06-04
Your driver isn't properly installed if it's using the Mesa driver, Twilight in Zero (I usually just copy and paste names - I think it's rude to get them wrong, and copy and pasting them makes sure you get them right!).

It should show someting like this if the driver is correctly installed:```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT
OpenGL version string: 2.1.7412 Release
```i.e. it should show ATI OpenGL and identify the card.

How did you install it?

---

### Post by Twilight in Zero on 2008-06-04
I installed it from the Hardware Drivers dialog in System -> Administration. A funny thing; the fglrx control panel doesn't work either. It claims that the ATI drivers aren't present or aren't installed right. :/

---

### Post by acoustibop on 2008-06-04
The ATI Control Centre is correct; your driver isn't properly installed, Twilight in Zero.  This is odd; I've had problems installing the ATI driver with other methods, but never with the Hardware Drivers or, previous to that, the Restricted Drivers Manager.  What happens when you open Hardware Drivers again; does it show the driver as being enabled and in use?

---

### Post by Twilight in Zero on 2008-06-05
Indeed it did shouw that the driver was enabled and in use. I did some research though, and it seemed as if xgl was somehow causing it to report that the mesa drivers were in use. So I removed xgl. But I still wanted Compiz. So I downloaded EnvyNG and ran it to tie up any loose ends I may have made and let it mess with Compiz, and whatever else it did.

fglrxinfo does now report correct info. The Catalyst Control Center runs (nothing useful to configure there, though). I don't even need to run ZSNES with the nonXgl script anymore. It performs the same whether I use the script or don't use it. But that performance is still the same as it was. :/

If it helps at all, here's the new fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

---

### Post by Villa Vampiria on 2008-07-16
Have you checked your cpu load while running ZSNES?

I have a simular problem with ZSNES running slow and laggy. I found out that my CPU-load is at 100%, and most of it is taken by the process Xorg, which is a grafical thing, right? (Mind you, I haven't loaded a ROM yet, it starts loading the cpu when I start ZSNES).

It ran smoothly on Ubuntu 7.10, but then I had to do a few updates (not the upgrade to version 8, just a few small updates) and after that, I got this problem.

It's a pity I can't remember what was updated...

---

