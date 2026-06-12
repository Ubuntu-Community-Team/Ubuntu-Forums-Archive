---
title: "Desktop failure at start up"
date: 2012-12-10
forum: Desktop Environments
---

### Post by worcesterman on 2012-12-10
I have a common problem on both my Ubuntu installations. After log-in the top and side menu bars briefly appear then vanish and I cannot restore them. I can do very little other than hardware power-off.
Has any one else had this problem and found a fix?  Meanwhile back to Windoze!

---

### Post by Roger E Critchlow Jr on 2012-12-10
I've had the same problem since this morning.  Ubuntu 12.10, login and there is no desktop sidebar and no top bar, no way to run anything.

Switch VT's and login to a terminal session, I can't find any logs that explain what's gone wrong.

-- rec --

---

### Post by zombifier25 on 2012-12-11
Press Ctrl + Alt + T to bring up a terminal, and try launching Unity manually from it.
```
unity
```
See if there are any errors. If it still cannot launch, reset Unity's profile:
```
sudo apt-get install dconf-tools # to install dconf
dconf reset -f /org/compiz/ # the actual reset command
```
This is for 12.10 . For 12.04, this will do:
```
unity --reset
```

---

### Post by Roger E Critchlow Jr on 2012-12-11
Thanks for the suggestions, I'll give it a try once I boot back into Ubuntu from Mint.

Ctrl-Alt-T is one of the emacs commands (transpose symbols) that the desktop has been hijacking for years that I always disable, but I'll get a terminal started somehow.

-- rec --

---

### Post by Roger E Critchlow Jr on 2012-12-11
That identified the problem: unity was not installed.  

Thinking back, I think unity was listed by synaptic in the "Local or obsolete" category a while ago and may have been auto-removed, but managed to limp along in memory until the machine was rebooted.
 
All better now for me. Definitely not the same problem that Worcesterman originally reported, but the fix might help him figure out what's happening.

Thank you very much,

-- rec --

---

### Post by LuisGMarine on 2012-12-11
If the above doesn't work for the thread originator, then go ahead and try this:

```
sudo apt-get clean
sudo apt-get install linux-headers-generic
sudo reboot
```

I'm not 100% sure I understand what the cause of the problem is, but I've also booted into nothing but a wallpaper.  I was able to get the panels back and everything after I ran those commands and restarted the machine.

From what I understand is that the nvidia drivers need to build some kind of modules that required the linux-headers-generic package to be installed.  For some reason this is not installed by default.  This info could be wrong, however if someone can give a better more "techy" explanation that would be helpful.):P

---

