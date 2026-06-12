---
title: "Installing DOOMSDAY Doom Engine"
date: 2010-01-24
forum: Gaming &amp; Leisure
---

### Post by deamon_knight on 2010-01-24
Looks like this is a great source port for Doom/Doom2/Heretic/Hexen et.al. 

[http://dengine.net/]("http://dengine.net/")

and I still have my Doom disks! However, I can't figure out how to install this. Its not in the repos and while their appears to be ubuntu packages those don't include the startup script and I can't figure out how get it. can anyone tell me how to set this up properly, especially for multiplayer?

Thanks,

---

### Post by KuriKai on 2010-02-03
Unfortunately multiplayer does not work in the 1.9 beta's it works in version 1.8.6 but it does not work in linux

you can install the latest beta on by adding the repo's found on the linux download page

this is the script I sue to run it
```
/usr/local/bin/doomsday -game jdoom -iwad /home/dave/Games/Doom/doom.wad -file /home/dave/Games/Doom/musicjdmu-doom.pk3 -width 1280 -height 1024

```

---

### Post by MindFusion on 2010-02-04
You can download it in a debian auto-install package from [http://www.playdeb.net/](http://www.playdeb.net/) i believe.

---

### Post by deamon_knight on 2010-02-05
Adding the Repos didn't work for me when I tried. I'll look at the installer, but you stable version 1.8 whatever does not work with linux, only the beta 1.9? and I can't find any hots for doom or doomsday from playdeb. Guess I'll hvae to wait for their server to come back up.

---

### Post by DoktorSeven on 2010-02-07
I have an i386 package of Doomsday 1.8.6 built in an older version of Ubuntu available [here](http://sites.google.com/site/sdcofer/); should install on 32-bit Ubuntu okay and on 64-bit with 
```
sudo dpkg --force-architecture --force-depends -i deng_1.8.6_i386.deb
```

You will likely need to make sure to install timidity as well, I've seen doomsday freeze if timidity isn't installed.

---

### Post by deamon_knight on 2010-02-19
Thanks DoktorSeven, I haven't installed your package yet, as I have a question. I thing I found the current repos for the 1.9 version of doomsday and have that installed but I can't get the launcher script "snowberry" to run. Do I need this your for package as well? Or am i completely lost on how this is supposed to work. I received any answers at all from Doomsdays forums, unfortunately.

---

