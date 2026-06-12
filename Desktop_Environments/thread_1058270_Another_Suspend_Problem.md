---
title: "Another Suspend Problem"
date: 2009-02-02
forum: Desktop Environments
---

### Post by h3xlas3r on 2009-02-02
Hello everyone! I finally made a complete switch from Windows to Ubuntu a few days ago after testing Ubuntu since 6.06 :). But even though I managed to get my sound working and installed the nVidia proprietary driver version (180), my computer acts funny when trying to go into suspend mode (suspend to ram or S3 as set in BIOS) :(.

I have read lot's of topics and searched over the Internet doing different tweaks to ubuntu and my BIOS to no avail (I have set these back to normal after tweaking).

When I press the power button on my computer or simply select suspend from the menu at the top right corner, my computer starts to go into suspend but then it wakes up right after. I see a black screen with scrolling text going downwards but can't make out what it says cause it happens to fast. My keyboard and mouse light up and I'm asked to enter my password. I do just that and I'm returned to my desktop with everything working normally, no disconnects or anything.

Some info about my system:

Computer Type: Desktop Computer

OS: Ubuntu 8.10 32-bit
Motherboard: ASUS P4P 800 SE
CPU: Intel Pentium 4 HT
Graphics Card: BFG GeForce 6200 OC 256MB AGP
RAM: 1GB
Monitor: 17" Compaq FS 7550 CRT

NOTE: I do NOT have a Compaq computer, my computer is custom from a local computer store.

I'm still new so please go easy on me ;). If you need any more info, like from the Terminal or more about my computer, please feel free to ask. I should also mention that I have done the DynamicTwinView FALSE tweak in the xorg.conf file because after installing the nVidia drivers, my refresh rate was at 50hz (which looks like 85hz cause it wasn't flickering).

Also with the drivers I noticed that 1024x768 is the only highest resolution that I can pick, which is fine since I use that resolution @85hz. But WITHOUT the drivers I can select higher but then again I don't bother with anything higher then 1024x768 so I don't think this is a problem.

Hope someone can help me with this cause suspend is something that I use to use a lot in Windows XP PRO. Please give me any type of tweak because I will try anything at the moment even if it's something I already did.

---

### Post by h3xlas3r on 2009-02-03
UPDATE: I have done some further testing by deactivating the proprietary drivers and using the open source ones. Basically same thing happens, computer goes into suspend but then wakes up with the mouse and keyboard lights ON. But this time my monitor doesn't work.

I've tried the 96, 173, and 177 drivers and they don't work either. Basically with the proprietary drivers, computer tries to suspend but wakes up as soon as it does and asks me for a password. Using the open source drivers, the computer tries to go into suspend mode but wakes up as soon as it does but this time the monitor doesn't work.

If anyone can give me a hint or tweak, I would greatly appreciate it.

---

### Post by h3xlas3r on 2009-04-29
So after quiting Ubuntu for awhile till this problem got fixed, I decided to give WUBI 9.04 a try. So I installed it and gave it about 4gb of free space and all seems good so far. Yet with all the updates and claims of 9.04 fixing the suspend problem on some computers, it still doesn't work on mine :(.

I know WUBI doesn't support Hibernation but it didn't say anything about Suspend or Suspend to RAM (S3). So that being said, is there anything I can do to fix this problem on my hardware? I am using the 180.44 drivers for nVidia and haven't changed any of my hardware since my first and second post on this thread.

---

