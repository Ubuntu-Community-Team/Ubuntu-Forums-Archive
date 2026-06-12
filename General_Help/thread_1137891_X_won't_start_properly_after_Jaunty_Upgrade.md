---
title: "X won't start properly after Jaunty Upgrade"
date: 2009-04-26
forum: General Help
---

### Post by jwbrase on 2009-04-26
I was using 8.10 Up until a day or two ago when I upgraded to Jaunty.
Everything went fairly well for a bit, though I had to reinstall some programs
that had been removed by the upgrade (such as Xscreensaver). Just last night I
noticed that certain programs (such as System log and Gnome terminal) weren't
starting, and tonight when I booted into Ubuntu X failed. It started, but it
won't go beyond a black screen with a mouse and give me a login screen. 
Fortunately, unlike Windows, Linux has multiple tty's, and I downloaded w3m
recently, so I was able to post about this problem without even having to 
reboot into XP. Suggestions?

EDIT: I guess at this point I can say I am (very temporarily) going back to
Windows. :)  Not as a "linux sux im running back to mommy microsoft" thing, but as
a "While I wait for help, I may as well use a GUI so I can use a mouse in my
browser" thing. If nobody has any better ideas, I will probably bust out my
Puppy USB to backup my Ubuntu files, then to my GParted LiveCD to reformat my
drive, and then back to Ubuntu 8.10.

---

### Post by jwbrase on 2009-04-26
I don't like bumping, but this is a fairly serious problem. Can anybody think of any solution other than wipe and reinstall?

---

### Post by jwbrase on 2009-04-30
I just tried booting into recovery mode, and if I go into the root shell from the recovery mode menu and use startx, it will partially load up LXDE. When I first tried doing this, LXDE started up, but the mouse wouldn't work, no background loaded, and I got an error message, the content of which was something along the lines of "Could not connect to <something> do you have <something> or <something> installed and running?". Also, when I switched out to a tty, the keyboard wouldn't respond. (It would respond to system commands like alt-f1 and ctrl-alt-del, but not to my attempt to type anything at the terminal.)

Seeing that LXDE had started up reminded me that re-installing LXDE had been one of the last things I'd done before X fell apart on me. So I uninstalled the lxde and lxde-core packages with apt-get. The only problem is that after doing this, when I type startx from the root shell, it still loads up LXDE, this time without the error message, and with the default LXDE background, but still with an unresponsive mouse. Also, when I switch out to a tty, I now get nothing but a blinking cursor in the top right corner, rather than a login prompt.

When I do a normal boot, the problems are all the same as before, X loads to a black screen, and GDM doesn't start up, so I can't log in graphically. Switching to a tty allows me to log in at the command line.

---

### Post by emarkay on 2009-04-30
WHAT VIDEO CARD?  (also what type of PC?)

Between NVIDIA and ATI and Intel, there are separate issues regarding them.

---

### Post by jwbrase on 2009-04-30
Dell Optiplex 755, with an ATI Radeon HD 2400 Pro Video Card, 128 MB.

I don't think it's a video card issue because the trouble didn't start immediately after I'd uprgraded (it took a day or two, I think), and I'd expect it to have started immediately if it was hardware-related trouble. I'm suspecting some sort of software-related cause, but I'm not sure what.

---

### Post by jwbrase on 2009-04-30
The Jaunty Live CD boots to GNOME with no problems.

---

### Post by emarkay on 2009-05-01
> **jwbrase said:**
> The Jaunty Live CD boots to GNOME with no problems.

Yes, but that is using the "default" video drivers - as soon as you get the ATI drivers (proprietary or internal), then it's the issue I am having.

Are you saying that you have panels and a properly sized video display, after a reboot, in 9.04, and an ATI HD  card? (Some others, including myself cannot - then we'll get to the issues beyond that...)  If so, how did you achieve this - what driver are you using - what is your display resolution set at?

This is the thread that is focusing on all of this:
[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

Thanks

---

### Post by jwbrase on 2009-05-01
> **emarkay said:**
> Yes, but that is using the "default" video drivers - as soon as you get the ATI drivers (proprietary or internal), then it's the issue I am having.

Are you saying that you have panels and a properly sized video display, after a reboot, in 9.04, and an ATI HD  card? (Some others, including myself cannot - then we'll get to the issues beyond that...)  If so, how did you achieve this - what driver are you using - what is your display resolution set at? 

Well, I did before X totally failed on me. I didn't really "achieve" it. I just made the upgrade, rebooted, everything was fine, I used it for a day or two through several boots, and then, one day on boot-up I got the problem described in my first post. Black screen, with the mouse showing up and working, but X not going beyond that and giving me GDM. (FWIW, the mouse I get at that point is a GNOME style mouse.) 

I was getting panels and a proper display resolution before it all went to pot, and now I *think* I'm getting proper display resolution, but I can't log in so I can't check if it's giving me panels or not. When I did startx from the root shell in recovery mode and got LXDE, I was getting a panel, etc, though.

I was using either the driver that I'd had on 8.10, or else whatever Jaunty upgraded it with (if it performed an upgrade it didn't say anything about it). My display is 1600*900. 

> 
This is the thread that is focusing on all of this:
[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

Thanks

Doesn't seem to apply to my problem. You have a list of affected cards in post 133 of that thread, and the closest one listed to my card is the Mobility Radeon HD 2400 XT. Mine is the Radeon HD 2400 Pro. The upgrade didn't say anything about drivers, and did work properly for a while before it died.

---

