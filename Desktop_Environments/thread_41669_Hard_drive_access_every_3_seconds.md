---
title: "Hard drive access every 3 seconds"
date: 2005-06-14
forum: Desktop Environments
---

### Post by oakhilltop on 2005-06-14
I just installed ubuntu a few days ago and am noticing my hard drive is being accessed every few seconds. At the moment I'm running gnome. I'm not sure if it does it under kde also.

How do I determine which daemon is doing this, and how do I stop it?

Thanks

---

### Post by fishfork on 2005-06-14
I find this as well. It's very noticeable as the disk on my laptop is quite noisy. One way to shut it up is:

```
sudo laptop-mode start
```

This should considerably reduce the amount of drive accesses.

---

### Post by electrosoccertux on 2005-06-14
I believe this is the journalized file system journaling itself. I'll probably turn that on even on my home computer; it might increase my hard drive life. No?

---

### Post by lotusleaf on 2005-06-14
[QUOTE=oakhilltop]I just installed ubuntu a few days ago and am noticing my hard drive is being accessed every few seconds. At the moment I'm running gnome. I'm not sure if it does it under kde also.

How do I determine which daemon is doing this, and how do I stop it?

Thanks[/QUOTE]

Me too, about every other second, and I have a desktop not a laptop so I'm wondering what's causing this. On a SUSE box I just disabled some hardware detection applet and it stopped, but it doesn't stop on Ubuntu and I'd like to figure out how to do it so I can stop other people from asking me the same question after I've installed Ubuntu for them. :)

---

### Post by skoal on 2005-06-14
[QUOTE=lotusleaf]Me too, about every other second, and I have a desktop not a laptop[...][/QUOTE]
sudo /etc/init.d/dbus-1 stop

* I'm pretty sure somewhere along that script the "hal" daemon gets launched and in conjunction with the systemwide daemon broadcasting hardware/application changes, your drive skips to the beat of an old 80's Dead or Alive classic, "you spin me right round baby, right round..."

I haven't spent the time thumbing through the init bash scripts yet, but these 2 are the culprit.  I have my own custom init level without these 2 and my drive is quieter than a mouse wearing socks in church.  However, when you start Gnome from now on, you will get a d-bus error and lose some functionality while not running these 2 inits.  I use XFCE anyways and it's not an issue 4 me anymore...

\\//_

---

### Post by lotusleaf on 2005-06-25
[QUOTE=skoal]sudo /etc/init.d/dbus-1 stop

* I'm pretty sure somewhere along that script the "hal" daemon gets launched and in conjunction with the systemwide daemon broadcasting hardware/application changes, your drive skips to the beat of an old 80's Dead or Alive classic, "you spin me right round baby, right round..."

I haven't spent the time thumbing through the init bash scripts yet, but these 2 are the culprit.  I have my own custom init level without these 2 and my drive is quieter than a mouse wearing socks in church.  However, when you start Gnome from now on, you will get a d-bus error and lose some functionality while not running these 2 inits.  I use XFCE anyways and it's not an issue 4 me anymore...

\\//_[/QUOTE]

Thanks, that's a great solution which I tried while running Fluxbox instead of Gnome.

---

