---
title: "New Video Card Results in Black Screen"
date: 2011-08-20
forum: Desktop Environments
---

### Post by Wadcutter on 2011-08-20
My EVGA 7600GT video card suddenly died. A friend gave me an EVGA GeForce 8400GS to replace. I'm running a homemade AMD Athlon 64 3700 box with 2 GB memory and 2- 250 GB WD hard drives. First drive has Win XP OS and second drive runs Ubuntu 10.04. I was using Ubuntu about 99% of the time before the video failed. After installing new vid card, I deleted old driver in Win and installed new driver off the CD that came with the card. Windows system was then 100% back to normal.

My grub booter is set up to default boot to Ubuntu with Windows the last choice which can be done manually. After installing new Win video driver and confirming it worked, I re-booted the computer and let it go to Ubuntu. The results was the usually flashing cursor for about 10 seconds, but instead of the Ubuntu splash screen popping up, the monitor went black for about a minute and then shut off the same as if I had shut down the computer.

That was over a week ago, Since then I have tried everything I can think of but nothing changes. I have read and tried numerous ideas from other posts on these forums (such as hitting ctrl, alt, +/- to change screen resolution) but I still have a black screen.

I tried booting up from my original install CD which is ver 9.10, not 10.04 (I upgraded to 10.04 by directly downloading online and never made a 10.04 CD). I can get into an Ubuntu desktop with that old CD and I checked to see that it showed the highest resolution for my monitor (a 22" wide flatscreen whose native resolution is high-1920x1280?? don't exactly remember at the moment). I also tried loading the generic Nvidia 185 driver but it didn't seem to take.  I downloaded the latest Nvidia driver for Linux onto a thumb drive and tried to install it here, but was refused because the message said it had to go into "root" and I didn't have  permission. I don't know how to establish permission when booting from an old install CD. I'm sure I have administration rights under my regular 10.04 installation but can't see it due to the blank screen.

I've tried at boot to go to the recovery mode listed right below the default Ubuntu boot option, but when I do, a whole series of text flashes on the screen and rolls down to the word "done" with a flashing cursor at the very end, The cursor flashes for about 5 seconds and then the screen goes black. I've tried to enter some quick text at the cursor to keep it from going black, but it doesn't stop it. It wants to go black and it does so.

I can probably get into a terminal from the old 9.10 CD, but have no idea what I would do once there. I'm not afraid of text commands--many years ago I used DOS regularly and was comfortable with text commands- but I just don't know Ubuntu/Linux commands nor do I have any idea of what the problem is and what I should be tweaking to fix it. I'm pretty much a Linux/ubuntu noob-I've been using it for about a year, but it has worked so well and so intuitively with almost zero problems, that I haven't really learned much about its nuts and bolts.

I would be grateful for any help (has anyone ever posted a problem on a forum and said otherwise?). I'd hate to have to re-install the whole OS because of one little video display problem. 

Thank you.

---

### Post by 3Miro on 2011-08-20
When you boot from a LiveCD, you live entirely in RAM. You can make changes to your Ubuntu install, but it can be tricky.

You should try to boot Ubuntu without the CD, but select "savemode" or "recovery". Try starting Ubuntu in low graphics mode. From there, you should be able to enter the default Gnome session (without effects). Go to System -> Admin -> Drivers and uninstall any Nvidia driver that you may have. Then reboot and you should be able to boot normally. After the reboot, install the Nvidia driver again.

---

### Post by Wadcutter on 2011-08-20
I'm not certain how to boot into a safe or save mode. If I ask for a command line in grub what command would I use to get a low graphics mode?  grub> _ ???

---

### Post by realzippy on 2011-08-21
Did you connect the power connectors to your new card?

---

### Post by 3Miro on 2011-08-21
Don't you have a Grub entry for Ubuntu recovery mode? You should have something like Ubuntu/Ubuntu (recovery)/Windows XP.

---

### Post by Wadcutter on 2011-08-21
realzippy: there are no power connections to this card. Additionally, it works fine in windows

3Miro: Yes, there are several entries but none of them work. If I try to boot into a recovery mode, a whole bunch of text rapidly scrolls by on the screen ending with the word "done" and then a flashing cursor. But nothing can be entered to the cursor (typing in text does not show up) and within about 5 seconds or less, the screen turns black and the monitor shows it is shutting down.

I have to leave now for the rest of the day and won't be able to reply to any posts until this evening (10-12 hrs from now). Thank you.

---

### Post by VanR on 2011-08-21
Try Ctrl+Alt+T to get a terminal. Then type in 

sudo apt-get install nvidia-current

---

### Post by realzippy on 2011-08-21
Since you have not uninstalled the nvidia driver on linux when
your 7600 died,this might be the problem.
boot the live the CD and delete the file /etc/X11/xorg.conf
on the filesystem of your harddisc.

---

### Post by Wadcutter on 2011-08-22
Dumb luck coupled with good advice from realzippy and VanR fixed this mess. My Grub booter listed several options, apparently each time Ubuntu was upgraded it listed a new boot option with an accompanying option to boot into a recovery mode for that version. None of them had worked for me (see above) but just by dumb luck I tried the oldest of the recovery mode options and I actually got a menu window that finally (after 9 days of cursing and wishing I had a racoon to kick) let me get into my system in a low graphics mode or perhaps a savemode. 

I then took realzippy's advice and deleted the config file and then tried to follow VanR's info about installing a new driver. At first it balked and said it couldn't find nvidia-current, but it ultimately loaded some kind of nvidia driver and I got a minimal resolution screen when I re-booted. I then tried to change the resolution to match the native resolution of my monitor (1920 x 1080)and struggled with that for half an hour because it said I couldn't use the Ubuntu program to change but should use the vendor's (nvidia) program. But ultimately the Ubuntu one was the one that worked and now I am back to at least 95-99.9% normal.

Many thanks to everyone who offered help. I hope that someday I may know enough to give someone else a hand up.

---

### Post by bapoumba on 2011-09-17
Thread marked as solved.

---

