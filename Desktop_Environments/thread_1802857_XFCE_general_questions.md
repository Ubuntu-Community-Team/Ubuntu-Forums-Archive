---
title: "XFCE general questions"
date: 2011-07-12
forum: Desktop Environments
---

### Post by SoFl W on 2011-07-12
I have performed some searches but didn't find the answers I was looking for.  I have an install of 10.4 with Gnome.  I recently added XFCE, however there are somethings I can't get working correctly.

1) I want the screen to lock automatically if the computer is inactive for xx minutes.  I am not necessarily looking for a screen saver, but that is how I have it set with Gnome.  I did not install xscreensaver.  Right now the screen blanks but does not require a password to get back to the desktop.

2) How do I edit the menu, disable or rearrange menu items?  In gnome the main menu program allowed this.

3) I have "Switch workplace using mouse" unchecked, yet the mouse scroll  still switches workplaces.  How do I *really* turn this off?

4) Compose Key options, how do I do them in xfce?  Example holding the compose key and pressing "o" "r" makes the registered symbol. ®  I did a search and it had a solution adding "XKBOPTIONS="compose:rwin" in the /etc/default/console-setup file but that didn't work.  I don't have a right win key so I tried, "lwin" but that didn't work either.  The only change was that when I hold the key down and press other letters they don't appear, where they did before that change.

Thanks

---

### Post by hhh on 2011-07-12
1) Usually people use xscreensaver to do this. You can also look at these programs...
[http://packages.ubuntu.com/lucid/xlockmore-gl](http://packages.ubuntu.com/lucid/xlockmore-gl)
[http://packages.ubuntu.com/lucid/xtrlock](http://packages.ubuntu.com/lucid/xtrlock)

2) Xubuntu 10.04 uses Xfce 4.6 which doesn't have a GUI for configuring the menu(s). You have to do that manually by editing the .desktop files in /usr/share/applications and the xfce-applications.menu file in /etc/xdg/menus (at least that is the directory structure in Debian, which I currently use). Basically, to remove, say, Gimp from the menu, in a text editor (as root) open /usr/share/applications/gimp.desktop and add NoDisplay=true to the bottom of the file and save it. More info here...
[http://wiki.xfce.org/howto/customize-menu](http://wiki.xfce.org/howto/customize-menu)

Apparently Xfce 4.8, which is part of the latest version of Xubuntu, has a GUI way of editing menus.

I can't help you with 3) and 4), I usually just use one workspace (you can disable others in Settings>>Xfce4 Settings Manager>>Workspaces or via the wWorkspace panel applet) and I've never needed 4). Sorry.

---

### Post by SoFl W on 2011-07-12
Thank you, I am not sure it is exactly what I wanted (#2) but I did learn something. I will take the time to read and explore that information.  You pointed me in the right direction and that will help.

#1 - I am a little worried on how it will work with my gnome screen saver.  Don't really need a screen saver, but I do need the screen to auto lock if I forget to lock it myself. 

Thank you.

---

### Post by hhh on 2011-07-12
Your first post didn't make it clear that you were using gnome-screensaver. That program has it's own screen lock feature. Launch gnome-screensaver-preferences. I'm not familiar with gnome-screensaver, maybe gnome-power-manager is required to get the screen to lock.

If that doesn't work, try replacing gnome-screensaver with xscreensaver.

I hope someone else chimes in here, I don't even use screen locking or screen savers as I'm on a desktop at home and it isn't necessary.

---

### Post by SoFl W on 2011-07-13
I am sorry, looking back I wasn't clear.  I see I chose [xubuntu] in the title, I should have selected [ubuntu] as that was the original install.  I have a 10.4 ubuntu install, I added Xfce recently.  I was not using the gnome screen saver in the Xfce environment. I was worried about xscreensaver messing with the gnome screen saver if I booted with gnome.

Screen locking is important, keeps people who shouldn't be messing with things from messing with them.  Although I have to worry about that less now, it is still something I would like to see work.

RE: The workplace switching with the mouse wheel.  That is now solved, there are two places to make the adjustment.   One is right clicking on the workplaces and selecting properties, the other is "Settings-> Window Manager Tweaks-> Workspace tab, and uncheck the first option "Use the mouse wheel on the desktop to switch workspaces"  I am not sure why it is in two places.

---

### Post by GSF1200S on 2011-07-13
> **SoFl W said:**
> I have performed some searches but didn't find the answers I was looking for.  I have an install of 10.4 with Gnome.  I recently added XFCE, however there are somethings I can't get working correctly.

1) I want the screen to lock automatically if the computer is inactive for xx minutes.  I am not necessarily looking for a screen saver, but that is how I have it set with Gnome.  I did not install xscreensaver.  Right now the screen blanks but does not require a password to get back to the desktop.
I actually went through a huge nightmare with screensavers in 11.04 recently. Gnome power management seems to be able to kill the backlight even while running in XFCE, but the only way I could ever get it to work was cycling xscreensaver anyways. I could not get the screen to lock automatically using gnome-screensaver- I had to manually lock it using: ```
xflock4
```
or
```
xscreensaver-command -lock
```
Keep in mind that Xscreensaver will work in Gnome and XFCE, including the ability to lock your screen and the ability to kill your backlight (in XX minutes). Since the general consensus seems to be that gnome-screensaver does not work well in XFCE, I suggest removing it and installing xscreensaver; your settings in xscreensaver are based off the .xscreensaver file in your /home/user folder, so xscreensaver will act the same in Gnome and XFCE:
```
sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver
```
Then, XFCE Menu--->Settings--->Screensaver (or run xscreensaver-demo from the command line) and set up your timeouts as you choose. On the first screen, select which Mode you want (blank screen, random screen saver, a particular one, etc), select the minutes interval you need, and check the lock screen after checkbox (even allows you to specify a different time interval than the screensaver itself). 

**EDIT** Make sure you check the Display Power Management checkbox on the Advanced tab if you want the monitor backlight to go off, if your computer supports the DPMS function..
> **SoFl W said:**
> 2) How do I edit the menu, disable or rearrange menu items?  In gnome the main menu program allowed this.
As another poster said, unfortunately XFCE 4.6 had no means to edit the Menu like Gnome does; you have to edit the .desktop files in /usr/share/applications directly in order to change the appearance of your menu. XFCE 4.8 allows the edit of its menu using Alacarte (a LOT of gnome-dependencies- fine in your case, but if you wish to use XFCE alone use-->) and LXMenuEditor. You might consider upgrading to XFCE 4.8 on your 10.04 install.. If you have a 32-bit system, you can go here:
```
http://www.webupd8.org/2011/01/xfce-48-ubuntu-1004-and-1010-ppas.html
```
and follow the easy instructions for moving up to XFCE 4.8, giving you menu editor capacity, among other things.

> **SoFl W said:**
> 3) I have "Switch workplace using mouse" unchecked, yet the mouse scroll  still switches workplaces.  How do I *really* turn this off?
I see you have this fixed :)

> **SoFl W said:**
> 4) Compose Key options, how do I do them in xfce?  Example holding the compose key and pressing "o" "r" makes the registered symbol. ®  I did a search and it had a solution adding "XKBOPTIONS="compose:rwin" in the /etc/default/console-setup file but that didn't work.  I don't have a right win key so I tried, "lwin" but that didn't work either.  The only change was that when I hold the key down and press other letters they don't appear, where they did before that change.
I have no experience with this, but I ended up on this page:
```
http://bapoumba.wordpress.com/2007/05/02/compose-key-with-xfce/
```
and the authors suggestion worked as did the responses listed in the comments section (only 3 comments total). You might try that..

> **SoFl W said:**
> Thanks
:)

---

### Post by SoFl W on 2011-07-14
I think I have finally worked through my questions/problems so I will answer them in case someone else has a question.  I have both Gnome and Xfce installed on my Ubuntu 10.4

> 1) I want the screen to lock automatically if the computer is inactive for xx minutes.  I am not necessarily looking for a screen saver, but that is how I have it set with Gnome.  I did not install xscreensaver.  Right now the screen blanks but does not require a password to get back to the desktop.As far as I can tell and as other people have suggested above the best way is to remove gnome screen saver and add xscreensaver. This will work in both Gnome and Xfce.
Something of note on the Xscreensaverscreen is that "Blank After" is how long before the screen saver starts, "Lock Screen After" is how long after the screen saver starts do you want the lock to activate.  "0" (zero) will activate the lock when the screen saver starts.
In the Startup applications keep an eye on gnome Power Manager and Xfce Power Manager.  I don't know of any problems but I would use only one.  They can be adjusted separately in Gnome and Xfce


>  2) How do I edit the menu, disable or rearrange menu items?  In gnome the main menu program allowed this.In Xfce 4.6 (and below) see the pose from "hhh" above.  In Xfce 4.8 (and above) there should be a menu option for it.


> 3) I have "Switch workplace using mouse" unchecked, yet the mouse scroll  still switches workplaces.  How do I *really* turn this off?There are two places to make the adjustment.   One is right clicking on  the workplaces in the panel, and selecting properties. The other is "Settings->  Window Manager Tweaks-> Workspace tab, and uncheck the first option  "Use the mouse wheel on the desktop to switch workspaces"  I am not sure  why it is in two places.     


> 4) Compose Key options, how do I do them in xfce?  Example holding the compose key and pressing "o" "r" makes the registered symbol. ®  I did a search and it had a solution adding "XKBOPTIONS="compose:rwin" in the /etc/default/console-setup file but that didn't work.  I don't have a right win key so I tried, "lwin" but that didn't work either.  The only change was that when I hold the key down and press other letters they don't appear, where they did before that change.I followed [Ubuntu's suggestion]("https://help.ubuntu.com/community/ComposeKey"), which didn't work for me but I did keep the changes I made and used [this suggestion]("http://forum.xfce.org/viewtopic.php?id=5995").

I also had another question and that was how do I turn on the num-lock key on by default.  I found the [answer here]("http://forum.xfce.org/viewtopic.php?id=3270").  Download a program called "numlockx" and create an entry in your startup programs with the command "numlockx on". 

Thank you to hhh and GSF1200S for their help.  Hopefully this will make someone else's Xfce experience more enjoyable.

---

### Post by hhh on 2011-07-14
No problem. BTW, I've never needed to add numlockx to the startup programs, it's always started for me automatically. There is a bug in numlockx where the keyboard light will reverse itself (LED is off when Num Lock is active and vice versa) but that's pretty minor.

---

### Post by SoFl W on 2011-07-15
I didn't understand it, in Gnome my numlock is on after boot.  I read about that bug, there is debate if it is numlockx or something else.  I have a wireless keyboard so it doesn't have any status lights.  I do have something for Conky that indicates caps/num lock status and that appears to be working correctly.

---

### Post by SoFl W on 2011-07-15
Has anyone installed 4.8 with 10.4 64bit?

I see the 32 bit option for 10.4, and I see a 64bit version for 10.10, but have not found a 64bit version for 10.4.  Attempting 4.8 upgrade on 10.4  gives me a partial upgrade error.

---

### Post by FormatSeize on 2011-07-15
> **SoFl W said:**
>  I did not install xscreensaver. Right now the screen blanks but does not require a password to get back to the desktop.
Isn't that awesome? Well, personally I enjoy not having to type my password every time I leave my desk for five minutes.

---

### Post by SoFl W on 2011-07-15
> **FormatSeize said:**
> Isn't that awesome? Well, personally I enjoy not having to type my password every time I leave my desk for five minutes.

No.  I want the screen to lock.

---

