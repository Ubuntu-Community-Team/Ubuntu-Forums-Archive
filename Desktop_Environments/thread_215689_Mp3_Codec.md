---
title: "Mp3 Codec ??"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Bellochka on 2006-07-14
I installed ubuntu 6.06.Everything's fine except amarok & rhythmbox music players.They can't play mp3.Do I need to install mp3 codec ? If I need where can I install it ?

PS:I can't find terminal.How can I launch it ?

---

### Post by TuxCrafter on 2006-07-14
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Welcome to Ubuntu :KS

---

### Post by TuxCrafter on 2006-07-14
ALT+F2 
insert >
gnome-terminal

Or 
Applications>Accesoires>Terminal

---

### Post by T700 on 2006-07-14
You can also go to the automatix link in my sig.  Automatix will install the codecs, along with other useful things.  You do, of course, have full control over what it installs.

Paul

---

### Post by Bellochka on 2006-07-14
[QUOTE=TuxCrafter]ALT+F2
insert >
gnome-terminal[/QUOTE]

Thanks it worked

[QUOTE=T700]You can also go to the automatix link in my sig. Automatix will install the codecs, along with other useful things. You do, of course, have full control over what it installs.[/QUOTE]

Well,I installed Automatix.So what should I do next ? There are many packages and I couldn't find anything like mp3 codec or mp3 plugin

---

### Post by T700 on 2006-07-14
Press Ctrl-F2 and type ```
automatix
``` and then press Enter.

Select what you want to install.  Press OK.  It will pause one or more time for you to enter your regular, user password.  Even though you can't see it being typed in the box, it is going in.  When the script completes (5 minutes to 1 hour, depending on what you download and your connection), you're done.  You can run it again later to add other things.

Paul

---

### Post by Bellochka on 2006-07-14
I think you didn't understand me.There many things and I don't want to download them.I only want to install mp3 codec and I can't find mp3 codec in here

---

### Post by Tamihania on 2006-07-14
...perhaps [EasyUbuntu]("http://easyubuntu.freecontrib.org/overview.html") will suite your needs better...? ;)

I hope it will be of a help,

tami

---

### Post by T700 on 2006-07-14
> **Tamihania said:**
> ...perhaps [EasyUbuntu]("http://easyubuntu.freecontrib.org/overview.html") will suite your needs better...? ;)

I think you are correct.

Paul

---

### Post by revelation.now on 2007-06-19
```
sudo apt-get install lame 
```

would be my first guess. Lame is an mp3 codec. It will also install as part of automatix if you get the Multimedia Codecs i believe.

---

