---
title: "First no menu bar, now even gnome gave up"
date: 2008-07-21
forum: Desktop Environments
---

### Post by wimmelis on 2008-07-21
Dear all, 


I am fairly new to ubuntu, and this morning when I booted my machine, I had not menu bars, so I searched the forums for help and tried several things (see below), unfortunately they did not solve my problem, but made it even worse.
As now, when I get the desktop login screen, my keyboard layout seems to have changed, which prevented me from logging in. Now that I found the special characters, I manage to log in, but only get a white screen as a reward for that, nothing else is happening or working, no right-click, no left-click no nothing.

Here is what I tried, in relation to the menu-bar:
1) some posts mentioned that right clicking would allow the choice of add panel, but I did not have this option.
2) I tried starting in recovery mode, and then continue booting from there, 
3)I also tried to repair packages in recovery mode, but it seems my network is not yet working, so no package repository can be contacted.
4) in recovery mode, I also tried to startx, as mentioned in some posts I came across, but that did not work either.
5) when booted into the normal system, I went to a terminal window, and did 
sudo apt-get update
sudo apt-get --reinstall install ubuntu-desktop
This did not help, so I tried by removing ubuntu-desktop first and then install again, but no luck either. 
6) When in normal boot, I also tried to kill the gnome and start it from another terminal, but to no luck, the system just hangs on a black screen.

System details: I am running hardy and have original ATI drivers installed and make use of dual screen configuration.

As far as I figured out from the posts I read, the cause of loosing my menu-bar is probably because I removed evolution, as I am using thunderbird instead, and wanted to save some disk space, but I don't quite get why this completely upsets my system like this. Though it should be reinstalled now as I did the ubuntu-desktop installation, which mentioned this package to be installed again.

Any help would be appreciated. And please try to be detailed, as I do not know short-cuts or so.

Many thanks, 


Regards,

Wim

PS: I was just about to start loving my complete swap to linux ...

---

### Post by tamoneya on 2008-07-21
unless you purge ubuntu desktop the configuration files remain. Try going to command line again and run:```
sudo dpkg-reconfigure ubuntu-desktop
```

---

### Post by wimmelis on 2008-07-21
Thanks for the proposal, I tried it, but it did not seem to change anything.

Meanwhile, I figured out that apparently I would need to get my default keyboard settings corrected for gnome (as that is why the login screen as the wrong keyboard layout). 

And it seems I can log into the failsafe gnome session, though I tried to set the default to become the normal one without any luck so far.

Anyone ?


Thanks, 

Wim

---

### Post by wimmelis on 2008-07-21
Problem solved, for completeness I will try to explain what I did, although I do not know exactly what helped.

The keyboard layout was solved by modifying my xorg.conf (in /etc/X11) to the right layout. 

I also reinstalled some of the gnome packages and reinitialised my ati-driver software (that might have been causing my white screen I think, as I had removed about all my configuration files, in an attempt to get the bad gnome ones out). 

next time I logged out and in again, things seemed to be working the old way.

Hope this might help someone, one day.

---

