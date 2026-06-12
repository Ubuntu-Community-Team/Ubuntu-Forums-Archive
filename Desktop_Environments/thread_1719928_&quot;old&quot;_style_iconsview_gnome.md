---
title: "&quot;old&quot; style icons/view gnome"
date: 2011-04-02
forum: Desktop Environments
---

### Post by jyates1 on 2011-04-02
Hi,

First time posting, long time fan

I recently got a new laptop, put in a couple partitions, installed windows in one and ubuntu 10.10 (64 bit) in another (ext4, 50GB, boot), left another partition for swap (6GB) and finally another for storage (160GB, ntfs). I'm also using an nvidia GeForce 460M with nvidia-current installed (version 260.19.06).

My problem is that all the icons (power "button", network manager, etc), general menus (e.g. in firefox) look "classic". That is to say not the "slick" appearance that I'm used to in the latest ubuntu.

I'm thinking it is something to do with either:
1) my X server config 
2) gnome install
3) general incompatability with latest nvidia driver 

I've looked through a bunch of different forum posts around nvidia and ubuntu (thinking this was the main source), but can't seem to find anything quite like this.

To no avail, I've tried:
1) Fiddling with the X server settings through the nvidia app
2) reinstalling gnome-desktop, gnome-panel
3) reinstalling the nvidia driver
4) installing compiz (much prettier special effects, not a solution to the basic problem)
5) Messing around with appearance settings.

Attaching an image of what the desktop looks like now.

Any thoughts? Thanks so much for the help!

---

### Post by Copper Bezel on 2011-04-02
So the panels, icons, and menus are all that default gray? Are the windows themselves themed, or are they in the default gray, too?

There's an issue that's been causing Gnome Settings Daemon not to run on startup on some installs. Try loading Appearance Preferences and see whether or not just running it restarts the theming. It's under Preferences -> Appearance.

---

### Post by jyates1 on 2011-04-02
The edges/container of the windows are themed, but the actual internal buttons are the default gray.

Pulling up appearce preferences made no apparent change to anything. Also tried switching the visual effects and theming around - no change to the issue.

Attaching what a firefox window looks like (similar to what everything else is too...)

---

### Post by cbowman57 on 2011-04-02
Run killall gnome-panel and see what it looks like when it respawns.

---

### Post by Copper Bezel on 2011-04-02
It's not just Gnome Panel, man, the *GTK theming* is completely gone. And this isn't the usual issue with Gnome Settings Daemon.

jyates1, if you open System Monitor, do you see gnome-settings-daemon listed in the Processes tab? If so, does killing it and re-running the process change anything?

---

### Post by ajgreeny on 2011-04-02
Just out of interest, what theme are you using?  I have seen all the icons you speak of and show, but that may be because I tend to play around and customise my theme, and lots of other bits and pieces of the desktop appearance just to get things the way I like and want.

For your information I use a customised Ambiance theme with a single bottom pale grey panel, but with the dark window title bar from Ambiance, and with the buttons on the right.  My icons are Ubuntu-mono-light.

It may not be what everybody likes, but it suits me!

See my screenshot for details.

---

### Post by Frogs Hair on 2011-04-02
See if this is related . [http://ubuntuforums.org/showthread.php?t=1575703&highlight=gnome+reverts](http://ubuntuforums.org/showthread.php?t=1575703&highlight=gnome+reverts)

---

### Post by jyates1 on 2011-04-03
@Frogs Hair  thanks for the pointer to the issue! Turns out it was exactly this - workaround for delaying the gnome-settings-daemon startup managed to make it work for me. 

@cbowman57, Copper Bezel no dice on the restart (though for no reason that I can figure out - based on the reason behind the above fix, that should be fine). 

Thanks everyone for the help!

---

### Post by cbowman57 on 2011-04-03
For the benefit of the next person that has this problem and wanders into this thread. What is the workaround for delaying the daemon?  

I scanned that link & I must have overlooked it.

> **jyates1 said:**
> @Frogs Hair  thanks for the pointer to the issue! Turns out it was exactly this - workaround for delaying the gnome-settings-daemon startup managed to make it work for me. 

Thanks everyone for the help!

---

### Post by Copper Bezel on 2011-04-03
I can't find it in there, either - I thought it came up somewhere around page 8. The idea is to add a script to Startup Applications like

```
sleep 10 &
gnome-settings-daemon &
killall nautilus
```

---

### Post by cbowman57 on 2011-04-03
@Copper Bezel, thanks, now we have it saved for posterity. :)

It sounds like the faster these machines get and the more people adopt SSD this will become more prevalent and this thread might become a handy reference.

---

### Post by jyates1 on 2011-04-03
Meant that it ended up linking to a solution on bugs.launchpad (though for some reason I can't seem to find it now :(. 

Long story short, the fix is in for Natty.  The problem was that the gnome-settings-daemon had a race condition with daemon that is run via Grub (I think) - the login screen has all the right appearances - but that daemon didn't shut down quickly enough and interfered with starting the daemon for the user desktop session. Interestingly, running a guest session gives you all the correct appearance goodness. It looks like the problems cropped up (mostly) from having the computer run too fast - most people were using Core i7s, an SSD and newish Nvidia card - and finding a race condition that hadn't cropped up on older generations of hardware.  

The possible fixes were:
 1) forced restart (tended to start the daemon using all the cpu and didn't work for everyone) 
```
killall gnome-settings-daemon 
gnome-settings-deamon
```2) (worked for me) Hack the startup values so the daemon has a lag time.  a. pull up /etc/xdg/autostart/gnome-settings-daemon.desktop. Should look something like: 
```

[Desktop Entry] 
Type=Application 
Name=GNOME Settings Daemon 
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon 
OnlyShowIn=GNOME; 
NoDisplay=true 
X-GNOME-Autostart-Phase=Initialization 
X-GNOME-Autostart-Notify=true 
X-GNOME-AutoRestart=true 
X-Ubuntu-Gettext-Domain=gnome-settings-daemon 
```b. Change Exec= to 
```
Exec=bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon" 
``` sleeping the daemon to give you some lag to so the other daemon can die first. Super hacky, but works. In Natty they have changed this so there is some checking to make sure the first daemon dies.

---

### Post by Krytarik on 2011-04-03
Nice workaround, really!! I wonder why no one else (of the Maverick users) came to that idea until now, maybe because it's indeed hacky. And you need to keep in mind that it may get reverted by future upgrades of gnome-settings-daemon. However, that is still much better than having it starting twice at login. This may prove being a real workaround, as long as the released fix doesn't get implemented to Maverick as well.

Greetings.

EDIT: Ah, actually there was: [http://ubuntuforums.org/showthread.php?p=10551292#post10551292](http://ubuntuforums.org/showthread.php?p=10551292#post10551292)
I forgot having seen that as a side note before, in the megathread. However, as also mentioned there, it seems not to work for everybody. I wonder why!?

---

