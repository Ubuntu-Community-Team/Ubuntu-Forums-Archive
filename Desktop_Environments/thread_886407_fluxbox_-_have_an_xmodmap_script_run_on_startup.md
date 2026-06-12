---
title: "fluxbox - have an xmodmap script run on startup"
date: 2008-08-11
forum: Desktop Environments
---

### Post by jetsabel on 2008-08-11
hi, i have a korean keyboard and i want to map the Hangul_Hanja key to mod3 on startup

i made a script /usr/bin/xmodmaphangulhanja 
```

#!/bin/bash
xmodmap -e "add mod3 = Hangul_Hanja"

```
this file is owned by root and rwxr-xr-x

this script works fine if i run it in terminal, but i need it to run automaticaly.
i have tried 4 ways so far and surprisingly, none work
1: @reboot xmodmaphangulhanja in my crontab
2: /usr/bin/xmodmaphangulhanja & in ~/.fluxbox/startup
3: xmodmaphangulhanja in ~/.xsession
4: @reboot xmodmaphangulhanja in root's crontab

any ideas?

---

### Post by kerry_s on 2008-08-11
man i haven't used that program in a long while, but from what i can remember you need to put the setting in "~/.xmodmaprc" and put "xmodmap ~/.xmodmaprc &" in the ~/.fluxbox/startup

which is what it looks like it says in "man xmodmap":
[http://www.manpagez.com/man/1/xmodmap/](http://www.manpagez.com/man/1/xmodmap/)

>        The filename specifies a file containing xmodmap expressions to be exe-
       cuted.   This  file is usually kept in the user's home directory with a
       name like .xmodmaprc.


---

### Post by jetsabel on 2008-08-11
thanks heaps! that did the trick :D

---

### Post by RedSquirrel on 2008-08-11
Some alternatives:

If you put the setting in ~/.Xmodmap, then gdm will load it for you automatically (if you're using gdm). If you login on the console and start X from there, you can put it in your ~/.xinitrc:

Excerpt from my ~/.xinitrc:

```

usermodmap=$HOME/.Xmodmap


if [ -f $usermodmap ]; then
    xmodmap $usermodmap
fi

```

---

### Post by jetsabel on 2008-08-11
thanks redsquirrel. i did what kerry_s suggested and it worked fine.
i had tried using ~/.Xmodmap but i was unaware of a .xmodmaprc file!

should have RTFM better O_o

---

### Post by kerry_s on 2008-08-11
> **RedSquirrel said:**
> Some alternatives:

If you put the setting in ~/.Xmodmap, then gdm will load it for you automatically (if you're using gdm). If you login on the console and start X from there, you can put it in your ~/.xinitrc:

Excerpt from my ~/.xinitrc:

```

usermodmap=$HOME/.Xmodmap


if [ -f $usermodmap ]; then
    xmodmap $usermodmap
fi

```


ah ha, milked another secret from red squirrel, i better add those to my notes. muhaha :lolflag:
interesting red, i've actually never seen it done like that in the .xinitrc, normally with scripts i would just execute them with the .xinitrc, but have the script in a file.
looking at that script, id probable just drop that as is in to .bash_profile.

---

### Post by jetsabel on 2008-08-11
yeah, seems to be almost infinite ways to do this and they can conflict with eachother.

i figured out what i did wrong; turns out that i DID know of the ~/.Xmodmap file, and it was loading my volume keys (i now vaguely recall setting that up in a late night wine-fueled config session :) 
so i guess that was loading and overwriting anything that i did at startup via other means >.<

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by kerry_s on 2008-08-12
> **jetsabel said:**
> yeah, seems to be almost infinite ways to do this and they can conflict with eachother.

i figured out what i did wrong; turns out that i DID know of the ~/.Xmodmap file, and it was loading my volume keys (i now vaguely recall setting that up in a late night wine-fueled config session :) 
so i guess that was loading and overwriting anything that i did at startup via other means >.<


:lolflag: it happens, i tweak mine so much when i need to set it back to default i forget what i changed. i usually use jwm though, i ditched fluxbox a long while back. i just built this desktop computer and wasn't familiar with the parts yet, so this time i just went with a full debian gnome install. i've got it running so well i don't think i'm going to run a custom install for awhile yet. now i'm just fine tunning it, trying to figure out what it can do, i've overclocked it from 1.5 to 1.7ghz, the max the bios will do, i also did some modding to keep it cooler, now i'm just putting it through it's paces. it looks like it will survive now, i got it from 45c to 75c down to 33c to 50c, hopefully it won't crash on me any more. i just created a launcher so i can check the temp:

```
#!/bin/sh
cat /proc/acpi/thermal_zone/THRM/temperature > ~/.cpu-temp
xmessage -center -file ~/.cpu-temp
```

anyways, glad you figured it out. :)

---

### Post by RedSquirrel on 2008-08-12
> **kerry_s said:**
> ah ha, milked another secret from red squirrel, i better add those to my notes. muhaha 
interesting red, i've actually never seen it done like that in the .xinitrc, normally with scripts i would just execute them with the .xinitrc, but have the script in a file.
looking at that script, id probable just drop that as is in to .bash_profile.

The approach is actually quite common. For example, if you Google "xinitrc", the first link is: [http://www.slackbook.org/html/x-window-system-xinitrc.html](http://www.slackbook.org/html/x-window-system-xinitrc.html). ;)

For anything related to X, I use ~/.xinitrc or possibly the "startup" file (or feature) of whatever window manager I happen to be running.

---

### Post by kerry_s on 2008-08-12
> **RedSquirrel said:**
> The approach is actually quite common. For example, if you Google "xinitrc", the first link is: [http://www.slackbook.org/html/x-window-system-xinitrc.html](http://www.slackbook.org/html/x-window-system-xinitrc.html). ;)

For anything related to X, I use ~/.xinitrc or possibly the "startup" file (or feature) of whatever window manager I happen to be running.

you know what it is, i think it's time to update my notes, i think i started these notes like 2 years back and let me tell you there a mess, i got chicken scratch all over the place, on one of them i wrote all the way around the edge :confused: you have to turn the page in a circle to read it, i figured i couldn't find nothing else to write on, but who knows, i can't remember why i did that. crap, i even have notes written with a grease pencil. (me, shaking my head). :lolflag:

you no what they say, every now and then you have to say screw it and start over. :)

---

### Post by statistic on 2009-04-12
Thanks for that kerry.

Right now I'm trying to find whatever tutorial it was I was reading where it told me to call my xmodmap.sh script that would run "xmodmap configFile" by putting it in /etc/profile.d. I want to tell everyone that's a BAD idea, it somehow forces you to log out on every login. I had to drop into the root shell to fix it.

Maybe a little off topic, but if anyone sees someone suggesting this, shout it down, it could really confuse a more newbie user.

---

