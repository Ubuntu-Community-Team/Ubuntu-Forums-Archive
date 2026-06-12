---
title: "Create new gnome sessions"
date: 2008-02-11
forum: Desktop Environments
---

### Post by deviouscontrol on 2008-02-11
Anyone know how to create a new gnome session?
I want to make one minimal session and one with all the eyecandy **** so I can just log in to whichever one. I can do this with different users and I was just wondering if i can do this using sessions.

---

### Post by deviouscontrol on 2008-02-26
hmm, 2 weeks with no answer, I guess this would be enough of a wait time to BUMP my own thread.

---

### Post by deviouscontrol on 2008-02-26
Alright, well either this isn't possible or I'm going about it entirely the wrong way.  Thanks for your help.

---

### Post by y-lee on 2008-02-26
Sorry this is first time I've saw this thread 

> Alright, well either this isn't possible or I'm going about it entirely the wrong way. Thanks for your help

I believe it is possible but i have never tried. you might want to see [CustomXSessions]("https://help.ubuntu.com/community/CustomXSession")

It is a bit dangerous because you are messing with important system files :(

So be careful.

Hope  this helps :)

---

### Post by deviouscontrol on 2008-02-26
thanks, any reply is helpful.

I've read through it and its starting to seem that this isn't an easy thing to do and probably not meant to be used this way.  I remember seeing a "safe" gnome session as opposed to the default gnome session that I normally log into so I thought it would be simpler.  Thanks again for your help.

---

### Post by y-lee on 2008-02-27
Sadly some things aren't easy.

You might be able to add a new session by the method used at [Dwm howto/tutorial]("http://www.xsnake.net/howto/dwm/dwm-eng.php#pt3") to add a DWM  entry to  the session manager, only do it for gnome. I don't know if that would work, but I've been playing with dwm today for the first time and I managed to add it to my session at boot. Only the name shows up as foo and I've been trying to change it to dwm with no luck :confused: that is how i found the last link i send ya btw. :lolflag:

**NOTE:** rcxdm restart (as root) as near as i can tell rcxdm is not a command I have nor a package i can find. I think that command just reboots anyway so I rebooted.

---

### Post by ryanhaigh on 2008-02-27
Depending on the changes you want between sessions you could have al your 'eye candy' apps in a little bash script mine is ~/.mystartups (the dot is so it's hidden). If you don't want them to run change to the terminal and chmod -x ~/.mystartups. You will also have to disable the associated things in system>prefs>sessions and add an entry for this script.

```

#!/bin/bash
compiz --replace --indirect-rendering &
yakuake &
pidgin &
thunderbird &
glipper &
deluge &
firefox &
#kdocker qtwengophone &
exit 0
```

---

