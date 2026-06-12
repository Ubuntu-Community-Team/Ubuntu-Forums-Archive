---
title: "Dark Oberon - Howto"
date: 2006-10-05
forum: Gaming &amp; Leisure
---

### Post by KillerKiwi on 2006-10-05
The grpahics in this game are cool plastercine any one :)


[IMG]http://dark-oberon.sourceforge.net/screenshots/2005-08-16_4_256x192.jpg[/IMG]

Compiling this from code was a bit of problem.... luckly I found some RPM's

Install Code
```

sudo apt-get install alien

wget http://www.polinux.upv.es/~vfernandez/suse/9.3/i586/dark-oberon-1.0.2rc1-1polinux.i586.rpm
wget http://www.polinux.upv.es/~vfernandez/suse/9.3/i586/libfmod-3.74.1-1polinux.i586.rpm
wget http://www.polinux.upv.es/~vfernandez/suse/9.3/i586/libglfw-2.5.0-1polinux.i586.rpm

sudo alien -i *.rpm


```

You should now have a menu item under Applications -> Games -> Dark Oberon

web site [http://dark-oberon.sourceforge.net/](http://dark-oberon.sourceforge.net/)

---

### Post by henriquemaia on 2006-10-05
Thanks for the HowTo. 

Just a small suggestion: when you alien packages, you can install them directly by typing:

```
sudo alien -i *.rpm
```

In this way you'll generate and install the debs in one step.

---

### Post by ed_agamemnon on 2006-10-05
does anyone know if this game is internet multi-playable yet?

---

### Post by henriquemaia on 2006-10-05
According to The Linux Game Tome, yes.

[Dark Oberon]("http://happypenguin.org/show?Dark%20Oberon")

---

### Post by Sp00ne on 2006-10-05
OMG a clay game, f**** awsome.

---

### Post by KillerKiwi on 2006-10-05
> **henriquemaia said:**
> Thanks for the HowTo. 

Just a small suggestion: when you alien packages, you can install them directly by typing:

```
sudo alien -i *.rpm
```

In this way you'll generate and install the debs in one step.

Cheers :), I updated the code

---

### Post by BathroomNinja on 2006-11-12
Thank you.  I was having a real heck of a time trying to compile this on my own.  I guess that's why we have the search feature ;)

---

### Post by webmadman on 2006-12-02
Thanks, that worked like a charm, look forward to getting lost in this :-)

---

### Post by p0wertrip on 2006-12-02
Just tried the game, and it´s really fun.
Thanks for the HowTo, KillerKiwi!

---

### Post by k1001001 on 2006-12-13
Thanks for posting this. They should just have these listed on the website instead of trying to compile the code, which judging by the help forum, has not really worked for many people (including myself). When I play though, the game is severely laggy. Any clue as to what the problem could be?

---

### Post by smartbei on 2007-05-01
The files are no longer hosted. wget returns 404 error.

---

### Post by Perfect Storm on 2007-05-01
Try here: [http://www.getdeb.net/category.php?id=1](http://www.getdeb.net/category.php?id=1)

---

### Post by Morbett on 2007-05-03
Hi, I installed those two .deb files and it installed properly.  When I launch Dark Oberon, it never loads up.  There's just a minimized window in my Window List that stays there forever and no game screen appears.  Any ideas?

---

### Post by SiemonG on 2007-05-07
Got the same problem here. Launcher doesn't do anything. Desktop freezes. Have to switch to another TTY and  KILL the process. When I launch Dark Oberon from a terminal this is what I get:

simon@SimonLaptop:~$ dark-oberon
Info: Loading configuration from '/home/simon/.dark-oberon/config.cfg'
Info: Loading data
Info: Loading textures from 'dat/fonts.dat'
Info: Loading textures from 'dat/gui.dat'
Info: Loading textures from 'dat/cursors.dat'
Terminated
simon@SimonLaptop:~$ 

I'm running Feisty on a Dell inspiron 6000
I've got the .deb packages from:
[http://www.getdeb.net/category.php?id=1](http://www.getdeb.net/category.php?id=1)
It's a shame it looks real good!

---

### Post by eoshicute on 2007-07-20
hi all, I want to ask something. When I play dark-oberon, I can't fight with a computer. If this game can't play in singleplayer mode and always multiplayer mode? thanks for sharing :)

---

### Post by eoshicute on 2007-07-21
I'm played dark oberon and I like it :) but I want to ask one question

is Dark Oberon don't have a singleplayer mode?

========================

please delete this reply, I'm made a double post

---

