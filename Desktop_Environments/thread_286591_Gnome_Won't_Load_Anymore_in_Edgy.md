---
title: "Gnome Won't Load Anymore in Edgy"
date: 2006-10-27
forum: Desktop Environments
---

### Post by odelay on 2006-10-27
[COLOR="Red"]Update:  I've found a workaround and explanation for my problem (see post #4).  It took me forever to figure out, so hopefully it'll save someone some time.  That said, I honestly don't understand the reasoning behind it, and don't know if it's a universal problem or just caused by some unfortunate combination of settings on my computer.[/COLOR]

What a terrible idea upgrading to Edgy has turned out to be.  It broke my ATI drivers, my wireless (after days of perfecting it in Dapper), and now, all of the sudden, it broke Gnome.  I'm really freaking out now b/c I can't get to *any* of my files and I really can't afford to reinstall everything.

OK, here's the deal.  I upgraded to Edgy yesterday, and have been working around trying to fix the video card and wireless problems.  Just as I've fixed both of them (in the way you fix a broken leg by tying a tree branch to it), I try customizing a theme.  I'm not even adding a new theme, just changing the combination of a preexisting one.  All of the sudden, all the windows, toolbar, and taskbar disappear.  All that's left is the desktop (and nautilus).  I can't open a terminal or application, and when I try to switch to another console via Cntrl + Alt + F2-F6 all the screens are garbled and there is essentially no command prompt to restart the computer.  I manually power down my laptop.

Upon starting up the next time, everything starts ok up to the login screen (even sound is working).  I enter my username/login and it goes to the Gnome loading screen.  The problem is, it doesn't load anything and sits there indefinitely.  Once again, I can't switch to any console and have no choice but to hold down the power button to restart.

2nd time, I tried starting up using the older kernel and the exact same thing happens.  Finally, the 3rd time I try starting up in Recovery mode.  It says something about being "Unable to find swap-space signature" and eventually gives me a root prompt.  This is where I'm stuck at.

All this frustration has nearly drove me insane.  If anyone could possibly help me, I'd really appreciate it.  About every 4-5 weeks my Ubuntu experience seems to hit a new low.  Everything was going so well right before Edgy though. :-|

---

### Post by odelay on 2006-10-28
Using the Dapper Live CD I was able to open GParted and check out what's going on.  Here's what I have

--> /dev/sda1    fat16    47.04 MB (this is the Dell Diagnostics Utility)
-->  /dev/sda2    ntfs    74.22 GB (this is my main Windows partition)
-->  /dev/sda3    ext3    16.75 GB (this is my main Ubuntu partition)
-->  /dev/sda4    extended    760.90 MB (this is/was my swap???!)
-->------> /dev/sda5    !unknown    760.87 MB

First, note that sda5 is actually *part of* sda4.  So apparently 760.87 MB of 760.90 MB is corrupted.  Furthermore, sda4 is listed as "Extended"  (not "ext3" or "ext2") instead of "Linux-Swap".  I don't know if this is normal, but it seems bad that GParted isn't recognizing the swap partition as a swap partition.  Any ideas here?

GParted allows me to reformat everything *except* the Extended sda4.  So I could reformat "Unknown" sda5 as Linux-Swap, but this whole situation is very screwy.  0.03 MB of Extended sda4 wouldn't be affected.

All this makes even less sense when you realize I was NOT doing anything out of the ordinary to cause this.  This did NOT happen directly after updating to Edgy, it did NOT happen directly after changing ATI drivers, and it did NOT happen after messing around with wireless.  It happened in the middle of switching to the Clearlooks theme.  What could I have possibly done that would even remotely affect the swap partition?

I'm really, really stressing out about this, and would appreciate any help.  One more thing to keep in mind is that I don't want to do something that could even possibly affect my Windows partition or prevent me from easily booting into it (with GRUB).

Thanks so much!

[COLOR="Red"]**Edit:
[/COLOR]I used GParted on the Live CD to format Unknown /dev/sda5 as Linux-Swap, rebooted into recovery mode and typed "sudo swapon /dev/sda5" to turn on the swap partition.  I ran the "Free" command to check, and it looks ok.

So, as of now, I fixed the swap partition error, but the Gnome problem is still alive and rampant.  There's a possibility that the swap was disabled/corrupted during the update, and I just didn't notice it until I read the startup output given from recovery mode.  This would essentially mean that the Gnome problem has nothing to do with the swap problem.

So now I'm back at square one...Gnome won't start.  In case anyone is listening (I hope someone is) another possible clue I noticed is that when the Gnome launch window comes up, the mouse icon is one that I last used yesterday (I changed it thereafter).  For some reason, Gnome is reverting back to an older setting (with the mouse, at least).  However, whatever it's reverting to isn't too old because my modified splash screen (put up a month ago) still shows up.  :(

---

### Post by lokey on 2006-10-28
I had a problem with Gnome starting up and then immediately crashing so I created a new user to see if the problem was with my user's settings and sure enough, the new user was able to load gnome just fine.

So using trial and error I found out that this file was crashing gnome:

**~/.config/autostart/thefuture.desktop**
```

[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=/usr/bin/thefuture
X-GNOME-Autostart-enabled=true


```

I did a 
rm -rf ~/.config
And gnome is working fine now.  Hope this helps!

-J

---

### Post by odelay on 2006-10-28
What a way to spend a night (as opposed to sleeping, maybe).  It's 6:30 a.m. and I think I'm finally figuring this out.  After getting on a 4-hour sidetrack of pretty much screwing up all my video settings (for no reason), trying to learn vi so I could edit some config files without a GUI, and messing around forever with xorg, I came across some success.  Luckily (for anyone with this problem other than me), the temporary fix is a little less painful.

**Cause**: (at least, I think):  In 6.10 going into the Theme Editor, and say, selecting "Silicon", then clicking "Theme Details..." then going to the Icon tabs and selecting "Default."  

**Problem**:  For me (this happened 2 out of 2 times in a row), this caused Gnome to essentially close everything (including the top/bottom menu bars) leaving only a blank desktop.  Trying to change consoles failed.  You're screwed; hold down the power button.

**Solution**:  I first tried it in safe mode, but it doesn't seem to matter--just click on whichever kernel you want.  Once you get into the login screen, enter your username and password, but don't press Enter yet.  Click on the middle button which allows you to select how you want to log into Gnome; the first time, select "Failsafe Gnome."  This should get you to a GUI, and a handful of errors popup (possible ACPI subsystem error, theme's may not work, etc.).  Go into the Theme editor and change the theme to something you know works--the icons probably won't change, but don't worry.  Restart again.  Enter your username/pword and select "3.  Gnome" this time--don't use "Last Session" yet.  If you're able to login correctly, you should be fine doing a regular login from hereon out.  If it's still messed up, I suggest repeating this again and keep fooling around with different theme/icon related things until it's fixed.

Observations:
*Issue seems independent of video drivers.  The first time I got it working I was using non-proprietary ATI drivers; 2nd time I got it working I was using proprietary ATI drivers compiled into the kernel (8.29 something).

---

