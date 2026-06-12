---
title: "My desktop is gone....Dell Mini 9"
date: 2009-02-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jaqrah on 2009-02-25
I have a Dell Mini 9.  I have been using all the tips and tricks from the Ubuntu Mini site.  I browsed over there and saw the article about Desktop Switcher. 

I downloaded the desktop switcher.  As soon as I tried to switch desktops, things started getting ugly.  I think there was some kind of conflict with compiz setting.  Weird transparency issues, is the window there or is not?

Then...nothing.  I all I have is my desktop wallpaper and nothing else.

Any suggestions would be helpful.  thanks

---

### Post by techstop on 2009-02-25
It sounds like you have a conflict between netbook-launcher and compiz. You cannot use both at the same time. Disable one of them and your problems should go away.

EDIT: For reference;

[http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html)

> Compiz-Fusion and Netbook Remix don't play nice together. You should disable Compiz from loading automatically on startup by following this howto

---

### Post by jaqrah on 2009-02-25
techstop thank for reply.  I used to use netbooks remix and then switched to a desktop with compiz.  I immediately regretted having not disabled compiz settings.

I did the following

```
sudo apt-get autoremove netbook-launcher
```

Unfortunately, my problem remains the same.  All I have is wallpaper and nothing else.

---

### Post by techstop on 2009-02-25
I think you removed the wrong thing...:wink:

From the link provided, it says compiz is not compatible with netbook remix, not just netbook-launcher. Maybe compiz is not compatible with the desktop switcher either?

Anyway, try this. Press Ctrl + F2. In the dialog box that pops up, enter "metacity --replace" (without quotes) and click Run. 

Is your problem fixed? If so, you need to disable Desktop Effects (compiz).

---

### Post by jaqrah on 2009-02-25
Okay...I cannot Ctrl/F2 (did you mean Alt/F2( I can't do that either)).  I am only able to enter code from failsafe terminal. So I cannot do as you suggested.

Previously I also

```
sudo apt-get autoremove desktop-switcher
```

I also removed netbook remix apps

```
sudo apt-get autoremove go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```

and still...no dice.  I think I will wait to hear from before I autoremove compiz.

---

### Post by techstop on 2009-02-25
Sorry, I did mean Alt + F2. 

This page describes your problem, and has a fix;

[http://www.ubuntumini.com/2009/02/repair-broken-xorg-file.html](http://www.ubuntumini.com/2009/02/repair-broken-xorg-file.html)

But it looks you've posted a comment there already?

Were you able to run "sudo dpkg-reconfigure xserver-xorg" as suggested? It's not clear from your comment what the problem was with that command...

---

### Post by sirebral on 2009-02-25
Compiz is likely the problem.  the mini 9 is not going to have a lot of video capability.

Why did you install desktop switcher?  The Workspace Switcher wasn't good enough?  Or is that what you meant?

Workspace Switcher comes with Ubuntu.  You just need to add the switcher to a panel.

**EDIT**:
Jaqrah.  You really should stop removing things until you get a better grasp on the problem.

---

### Post by jaqrah on 2009-02-25
techstop, yes I did follow the Xorg repair directions to the T, choosing everything in its default state.  I really wasn't sure what exactly was supposed to happen after following directions besides reboot.  The one thing I found odd about the Xorg repair was that every question was about keyboard default setups???? 

Sirebal, thanks for your advice.  Despite the lack of video capability of my Dell Mini 9,  I was running a desktop with compiz setting on high without any issues.  I think I tried to soar to close to the sun by trying to be able to switch from Notebook Remix desktop and a regular desktop with Compiz enabled.  

Also, I saw no harm in removing the Notebook Remix application and its dependencies.  No loss there in seeing if desktop would return to a workable state.  I did mention I wasn't going to remove compiz until I heard more advice.

---

### Post by jaqrah on 2009-02-25
With more research and brain time, I realized Xorg repair is not working properly for me.  I follow the directions provided.  I answer numerous questions about keyboard settings and then I am thrown back to failsafe terminal with this message:

xservice-xorg postinst warning:overwriting possibly-customised configuration file;backup in /etc/X11/xorg.conf.2009025111540

Apparently, I am not fully completing Xorg repair.  I am not able to get in there and repair the graphics settings due to this warning message.

As always, an help on this matter would be greatly appreciated.

---

### Post by sirebral on 2009-02-25
> **jaqrah said:**
> Sirebal, thanks for your advice.  Despite the lack of video capability of my Dell Mini 9,  I was running a desktop with compiz setting on high without any issues.  I think I tried to soar to close to the sun by trying to be able to switch from Notebook Remix desktop and a regular desktop with Compiz enabled.

Fair enough.  I think you are right, but I appreciate the certain level of insanity that proves people wrong and brings us new goodness.  Rock on, jaqrah.

Anywho..  Can you remove Compiz and and try that?  I am leaning on the side that Compiz is a little bigger then the Mini 9 is supposed to handle on a daily basis, so the software might be causing conflicts.

How did you get Compiz to work anyways?  I am still running the DellBuntu.  I have not taken the care to remove it since it is quite stable.

Also you might want to try a apt-get update or an apt-get autoremove then an apt-get update.

---

### Post by jaqrah on 2009-02-25
Sirebal...its fun to push things a little.  And hey its just a mini 9.  I am not sure I would have messed with my desktop with such abandon.

At this moment, compiz is disabled.  But I am feeling more and more confident I have a broken xorg.conf.  I am getting closer to the core of things but haven't quite got there yet.  Unfortunately, the easy fix 

```
sudo dpkg-reconfigure xserver-xorg
```

is not working.  But I have found some additional posts that are getting me closer to the heart of the matter.

To answer your other question, I dumped the Dellbuntu set up the day I received my Mini 9 and installed Ubuntu 8.10 with Notebook Remix theme.  I highly suggest visiting this site.

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

A few weeks ago I grew tired of the remix theme and turned it off.  I set up a more traditional desktop with a custom theme I downloaded from a gnome theme site.  At some point I enabled compiz and was using the "Cube" on my mini desktop as well as desktop widgets.  I wasn't having any issues until I tried to use the desktop-switcher that is mentioned in the above link.  Apparently, compiz and netbook remix don't work well together.  I just forgot that when I overzealously tried to reach for the sun.

---

### Post by sirebral on 2009-02-26
Well, you are not Icarus so you don't have to worry about drowning to death. :whew:

I myself was going to drop the Netbook remix in favor of Xubuntu.  I actually liked it though.  The Netbook remix has been very stable for me.  My 8.10 Studio Hybrid suffers from some audio issues.  Most likely because I have not taken the time to remove pulseaudio (which sucks).

What is this Desktop Switcher that you are talking about?  Do you mean the workspace switcher?  That comes installed and all you need to do is put it on a panel.

If everything worked until that point, maybe remove the desktop switcher you installed and then restart XORG (ctrl alt backspace).

---

### Post by jaqrah on 2009-02-26
Unfortunately, (ctrl-alt-backspace) doesn't help the issue any.  It does restart xorg but I still have a blank desktop.

There is something going on with xserver-xorg. If I do this

```
startx
```

I get the following error
```
 Fatal server error:  Server is already active for display 0
     If this server is no longer running, remove /tmp/.X0-lock and start again.
```

---

### Post by techstop on 2009-02-26
What happens if you do the following;

```
Ctrl+Alt+F1
``` to open tty1

```
sudo /etc/init.d/gdm stop
```

```
sudo dpkg-reconfigure xserver-xorg
```

```
sudo /etc/init.d/gdm start
```

???

---

### Post by sirebral on 2009-02-26
Sieg!  Good one techstop.

---

### Post by jaqrah on 2009-02-27
techstop, sirebral...thanks for all the assistance I greatly appreciate it.

I threw in the towel.  I had another thread going in the desktop sub-forum and plus on another site.  I wasn't getting any timely information.  For some reason, I kept getting a fatal error when I was trying to :

```
sudo dpkg-reconfigure xserver-xorg
```

at this juncture, the error really doesn't matter.

I am leaving town in a couple of days and I want this baby functional for the trip.  So I did a clean install last night.  Gave me an opportunity to repartition my /.  I was almost out of space.

So once again thanks for the help.

---

### Post by webkris on 2009-03-19
I have the exact same issue.
I was running maximus and metacity - so it's not a compiz issue.
I got the same error on the xorg repair...

I even un-installed the desktop switcher - which clearly "switches" something that can't be turned back on.

I think the answer lies in whatever "desktop switcher" does.
Hoping for help.

I certainly learned my lesson - stop typing in sudo install awesome-program without reading the fine print.

- Kris

---

### Post by jaqrah on 2009-03-19
webkris

Sorry to hear about your problem.  I also wished I hadn't just tried to do something cool.  I wonder if the problem lies in switching between two radically different types of desktop themes.  At what point did your desktop crash?

---

### Post by webkris on 2009-03-19
> **jaqrah said:**
> At what point did your desktop crash?

I switched...
I then opened the switcher to go back.
When I closed firefox I realized I had a big problem...

After 4 hours of head scratching - I cut my losses. :(
Hopefully someone can sort this out.

- Kris
Windows expert
Linux n00b

---

