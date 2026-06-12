---
title: "Long delay after logging in but before desktop appears"
date: 2010-05-22
forum: Desktop Environments
---

### Post by vek on 2010-05-22
GDM/Gnome/Greeter issue?

So after I enter the password and press enter, the login dialog disappears, the purple background stays.. and just stays... and stays... for about 20-30 sec.    Sometimes what looks like a panel (But stays completely blank) appears at the bottom of the screen for the duration.  

I remember at one point the panels and such would almost instantly appear, but now there's this huge delay.  What could it be doing?  And why is it doing those things instead of starting my panels?  Once my selected desktop wallpaper appears (instead of the purple stuff) it goes very fast, but it takes forever to get there... a 12 second boot doesn't help if you have a 20 second login.  Maybe its the various services starting up?  But if so, shouldn't it start my desktop/panels first?

---

### Post by wilee-nilee on 2010-05-22
Have you added anything to the startup applications in preferences or at least gone there to tick things off you don't need.

---

### Post by vek on 2010-05-22
> **wilee-nilee said:**
> Have you added anything to the startup applications in preferences or at least gone there to tick things off you don't need.

Thanks, I'll check to see if this could be the issue.

Although user-land startup apps honestly should not be starting BEFORE the desktop is present.  Its not very elegant and leads to confusion since it looks like thing thing is locked up... I mean, I understand services, but tray applications, mp3 players, etc?

---

### Post by wilee-nilee on 2010-05-22
> **vek said:**
> Thanks, I'll check to see if this could be the issue.

Although user-land startup apps honestly should not be starting BEFORE the desktop is present.  Its not very elegant and leads to confusion since it looks like thing thing is locked up... I mean, I understand services, but tray applications, mp3 players, etc?

You can set the added commands in the startup applications with a delay but I am not sure how.

We are not sure if the culprit is this startup program so time will tell.

---

### Post by vek on 2010-05-22
I tried trimming that list to only the essentials (no user defined ones, only the bare ones that come with Gnome, and even turned off some of those) and it did not seem to have any real impact on the start-up time.

Logging out and in again (Without restarting) is instantaneous, even with all my user-land applications enabled... so its only the first time when it boots up.

---

### Post by bobbythehun on 2010-05-22
I too am having this issue. Boot is extremely fast. Login is almost as slow as my windows 7 machine.  Please brothers, lets don't go down that road! Trimming start up applications did not help me either. Thanks in advance for everyones help.

---

### Post by Ron S on 2010-05-22
Same problem here on my desktop but not on my laptop. Desktop runs a nvidia graphics card while laptop has ati . With all the problems of nvidia and plymouth not playing nicely with each other I wonder if this is causing the problem . What graphics card are you all using and which driver do you have installed proprietary or free?

---

### Post by hok00age on 2010-05-22
> **Ron S said:**
> Same problem here on my desktop but not on my laptop. Desktop runs a nvidia graphics card while laptop has ati . With all the problems of nvidia and plymouth not playing nicely with each other I wonder if this is causing the problem . What graphics card are you all using and which driver do you have installed proprietary or free?

Is that problem still appears when you logged in with new user accounts? Test it.

---

### Post by Ron S on 2010-05-22
> **hok00age said:**
> Is that problem still appears when you logged in with new user accounts? Test it.
  If I log out and log back in again there is no problem. Desktop takes about 1 to 2 seconds to appear.

---

### Post by moongia on 2010-05-22
> **vek said:**
> GDM/Gnome/Greeter issue?

So after I enter the password and press enter, the login dialog disappears, the purple background stays.. and just stays... and stays... for about 20-30 sec.    Sometimes what looks like a panel (But stays completely blank) appears at the bottom of the screen for the duration.  

I remember at one point the panels and such would almost instantly appear, but now there's this huge delay.  What could it be doing?  And why is it doing those things instead of starting my panels?  Once my selected desktop wallpaper appears (instead of the purple stuff) it goes very fast, but it takes forever to get there... a 12 second boot doesn't help if you have a 20 second login.  Maybe its the various services starting up?  But if so, shouldn't it start my desktop/panels first?

try disabling your floppy disk in you bios..it work for me...hope it helps

---

### Post by Ron S on 2010-05-22
> **moongia said:**
> try disabling your floppy disk in you bios..it work for me...hope it helps
Yes thanks moongia disabling the floppy did the trick.Desktop loads in a matter of seconds now.

---

### Post by moongia on 2010-05-22
> **Ron S said:**
> Yes thanks moongia disabling the floppy did the trick.Desktop loads in a matter of seconds now.

no prob. glad it worked...i had that the same prob. with the beta 10.04..i just thought it was because it was a beta so no big deal,one day i went into my bios and saw my floppy was on,but i did not have one..so i disabled it,and the issue went away..lucky i guess..

---

### Post by bobbythehun on 2010-05-23
nvidia version 173;    GeForce 7300GS card;    monitor=samsung syncmaster

---

### Post by PostWax on 2010-05-23
Same problem here right after a fresh install of 10.04 64 bit.  No solution so far but I have a bit more information that may help.

After fresh install when I noticed the 20 second delay.  I kept loading the programs I wanted to have.  One of them is AWN.  After the next reboot still had the 20 seconds delay and purple screen but at the bottom was the AWN icons.  From there I could run Google Chrome.  It would load my home page while I was still waiting for desktop to load.

Still a nOOb but totally enjoying 10.04.  Thanks for your efforts.

---

### Post by gauchotodd on 2010-05-23
> **PostWax said:**
> 

After the next reboot still had the 20 seconds delay and purple screen but at the bottom was the AWN icons.  From there I could run Google Chrome.  It would load my home page while I was still waiting for desktop to load.



Interesting, no idea why that is but maybe someone else can address it for you.

But restart your computer, go into BIOS, and disable the floppy drive.  I had the same delay on login as everyone else, and this fixed it perfectly.  Takes one second now.

My other issue is that after grub chooses the OS, it sits on the black cursor screen for almost ten seconds.  Any ideas why that is, or how to fix it?

---

### Post by dementic on 2010-05-23
Look here... I solved the same problem by removing KDE and booting on another kernel, then on mine usual kernel again.

[http://ubuntuforums.org/showthread.php?t=1491226](http://ubuntuforums.org/showthread.php?t=1491226)

---

### Post by PostWax on 2010-05-23
IT WORKED!

I do not believe it! Disabling the Floppy in the my Bios solved my "Boot time issue" I dropped from 20 to 25 seconds after the password to 10 to 12 seconds.

Thanks so much to Dementic!!!

---

### Post by vek on 2010-05-23
I disabled the floppy drive in the bios and it did not help.

It got rid of a read error dmesg but doesn't appear to have actually speed up bootup.  I think it might be an nvidia issue but I'm not sure.

---

### Post by texaswriter on 2010-05-23
I haven't seemed to notice this on my Kubuntu 10.04 installation, perhaps because the floppy is already disabled. However, on my home pc which has Ubuntu 10.04 [Gnome], I have seen this occur when I boot up for the first time. 

I will try checking the BIOS to see if that helps. Either way, I will try to post the results.

Edit: Yes, did the trick!!

---

### Post by AlexMinsk on 2010-05-29
Disabling floppy did the work.
Thanks!

---

### Post by vt_antik on 2010-06-15
I'm surprised as well but I too have fixed the issue by disabling the floppy.

---

