---
title: "Is Medal of Honor Allied Assault a native Linux game?"
date: 2008-08-22
forum: Gaming &amp; Leisure
---

### Post by go_beep_yourself on 2008-08-22
I was reading on Wikipedia next to platforms that this game is made for Linux. Can anybody confirm it is true? If yes, how is it installed in Linux? 

[http://en.wikipedia.org/wiki/Medal_of_Honor:_Allied_Assault](http://en.wikipedia.org/wiki/Medal_of_Honor:_Allied_Assault)

---

### Post by doorknob60 on 2008-08-22
This help [http://icculus.org/~ravage/mohaa/](http://icculus.org/~ravage/mohaa/) ?

---

### Post by Sockerdrickan on 2008-08-24
openmohaa will rock, too

---

### Post by eragon100 on 2008-08-24
buy it from tuxgames: [http://www.tuxgames.com/details.cgi?&gameref=104]("http://www.tuxgames.com/details.cgi?&gameref=104")

It's temporarily sold out right now, but it will come back :wink:

---

### Post by go_beep_yourself on 2008-09-11
> **eragon100 said:**
> buy it from tuxgames: [http://www.tuxgames.com/details.cgi?&gameref=104]("http://www.tuxgames.com/details.cgi?&gameref=104")

It's temporarily sold out right now, but it will come back :wink:

I went and tried that. Any ideas why it doesn't work?? I tried running it in every possible way. Also where can the latest version of that installer be downloaded? I do have the game already.

```
chris@ubuntu:~/Downloads$ chmod 755 mohaa-lnx-1.11-beta3.run 
chris@ubuntu:~/Downloads$ sudo sh mohaa-lnx-1.11-beta3.run 
[sudo] password for chris: 
Verifying archive integrity... All good.
Uncompressing Medal of Honor: Allied Assault beta 3 for Linux......................................................................
chris@ubuntu:~/Downloads$ sudo bash mohaa-lnx-1.11-beta3.run 
Verifying archive integrity... All good.
Uncompressing Medal of Honor: Allied Assault beta 3 for Linux......................................................................
chris@ubuntu:~/Downloads$ ./mohaa-lnx-1.11-beta3.run 
Verifying archive integrity... All good.
Uncompressing Medal of Honor: Allied Assault beta 3 for Linux......................................................................
chris@ubuntu:~/Downloads$ sudo ./mohaa-lnx-1.11-beta3.run 
Verifying archive integrity... All good.
Uncompressing Medal of Honor: Allied Assault beta 3 for Linux......................................................................
chris@ubuntu:~/Downloads$ 

```

---

### Post by DoktorSeven on 2008-09-11
> **go_beep_yourself said:**
> I went and tried that. Any ideas why it doesn't work?? I tried running it in every possible way. Also where can the latest version of that installer be downloaded? I do have the game already.


The installer uses GTK 1.2; maybe you don't have that installed.  Use syaptic/apt-get/aptitude/etc to look for and install the GTK1 libraries and try running it again.

---

### Post by Vitamin-Carrot on 2008-09-11
Be Warned:

It does have sound issues

---

### Post by go_beep_yourself on 2008-09-11
> **Vitamin-Carrot said:**
> Be Warned:

It does have sound issues

Hmm, maybe that will be fixed in a future release of the installer if there's anymore to come.

---

### Post by DoktorSeven on 2008-09-11
The installer is just a graphical installer made from binaries written long time ago (and the installer itself is quite old!) -- last update was [September 2004.](http://icculus.org/betas/mohaa/)

I wouldn't hold your breath waiting on new versions.

---

### Post by go_beep_yourself on 2008-09-15
> **DoktorSeven said:**
> The installer is just a graphical installer made from binaries written long time ago (and the installer itself is quite old!) -- last update was [September 2004.](http://icculus.org/betas/mohaa/)

I wouldn't hold your breath waiting on new versions.

Are there any fixes for the sound issues or do you guys just play without sound?

---

### Post by revertex on 2008-10-20
there is no problem whit the installer, works flawlessly.

The problem seems you don't have OSS support enabled.

This should work.

```
sudo modprobe snd-pcm-oss
```

consider edit /etc/modules.

---

### Post by Sealbhach on 2009-07-28
> **revertex said:**
> there is no problem whit the installer, works flawlessly.

The problem seems you don't have OSS support enabled.

This should work.

```
sudo modprobe snd-pcm-oss
```consider edit /etc/modules.

OK, well I installed this today and it runs very nicely with the Linux Client. However, I still have a slight issue with sound, enemy fire or explosions sound really faint... ambient sounds are fine and my own fire sounds loud. I tried that fix mentioned here but nothing doing. Just wondering of anybody had found a way to fix these issues with the other sounds?

.

---

