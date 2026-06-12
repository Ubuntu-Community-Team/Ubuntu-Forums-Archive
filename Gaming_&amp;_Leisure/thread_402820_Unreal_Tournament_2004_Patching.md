---
title: "Unreal Tournament 2004 Patching"
date: 2007-04-06
forum: Gaming &amp; Leisure
---

### Post by showty on 2007-04-06
Hey everyone

I just installed UT2004 on my second Linux machine (woo hoo :D ) and it worked with only minimal lag on lowest detail (Athlon 1700+, 768MB RAM, Radeon 9600XT).

I downloaded the 3369.2 patch as I wanted to play online, but I can't get access to the .ut2004 directory (/home/mark/.ut2004). Thats where I think it was installed anyway (I just used the default location).

It says I need to be root to access that directory.. can someone either tell me where I'm supposed to put the patched files if it isn't .ut2004, or how I can put the patched files in .ut2004..

thanks :D

---

### Post by Drezliok on 2007-04-06
I believe that the .ut2004 folder is only where your settings are kept.


You don't have to put that patch anywhere.

Use this [http://liflg.org/?catid=6&gameid=17](http://liflg.org/?catid=6&gameid=17) on that page there is a MEGAPACK, it has all the updates wrapped into one and it's a linux based installers. Same command you used to install ut2004 is used to install this

---

### Post by fidolip on 2007-04-06
Drezliok:
for some reason I cannot download this file.:-( Although I downloaded other megapack as tar.bz2 and unpacked it. It contains a lot of folders (e.g. Animations, Sounds, System, Web etc.). Do you know how to install it manually?

EDIT:
Seems that it's enough to copy all the files into the ut2004 directory.:-)

---

### Post by showty on 2007-04-06
Yeah I couldn't work it out either, but I managed to copy the files over with the sudo command (love how Linux teaches you as you go..).

But now UT2004 doesn't start, complaining about a missing section in the .ini configuration file (it doesn't say which configuration file) and as I can't get in .ut2004, I can't see if I can fix it..

Any ideas?

---

### Post by showty on 2007-04-06
Does anyone know what I should do? Heres the exact output:

```
mark@mark-desktop:~$ ut2004
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History: 

Exiting due to error
mark@mark-desktop:~$ 
```

---

### Post by Perfect Storm on 2007-04-07
[http://gaming.gwos.org/e107_plugins/content/content.php?content.56](http://gaming.gwos.org/e107_plugins/content/content.php?content.56)


You properly made the classic mistake by launching the game right after the game installed by hitting the launch button from the UT2004 installer (which means you have messed up the permission of the folder and files of ./ut2004 in your home folder).

---

