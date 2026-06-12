---
title: "beryl with geforce 2 go"
date: 2007-04-08
forum: Desktop Effects &amp; Customization
---

### Post by abaybas on 2007-04-08
I have an old dell 8200 with a geforce 2 go, running ubuntu 6.10

When I tried using envy to install nvidia drivers, my X went black, and I had to revert in console. So I installed the nvidia drivers using automatix.

With those drivers, i installed beryl, and it all went fine. ( i even tried to see if I have direct rendering with glxinfo, and yes I do. )

when i start beryl, my screen gets scrambled. Sometimes, I can see the windows and the decoration, and if I drag it around I even see the cool wobbly effect. However nothing is legible. I end up having to kill X.

Any ideas on how I can get this working? I tried starting beryl-manager with the "no force window manager" option and playing with the advanced options but I don't know what I'm doing so that didn't help either.

Any help would be greatly appreciated. Thanks.

---

### Post by FuturePilot on 2007-04-08
Haha, I have that same laptop. Log in without running Beryl and do```
sudo gedit /etc/X11/xorg.conf
``` Go down the the "screen" section and make sure the default depth is set to 24 and not 16 then save the file. Log out and restart X with Ctrl+Alt+Backspace. Then try Beryl again. When I set up Beryl I had to change that manually. It sounds like that's the issue. By the way, does Beryl make your computer completely freeze after a short time? Every time I try running Beryl from the Nvidia drivers the whole thing freezes up after a few minuets. I have to use XGL to get it to work.

---

### Post by abaybas on 2007-04-08
Hah that's awesome. Changing the depth definitely worked. Thanks!
It's amazing what Beryl can do even with a 5yr old laptop.

It did freeze on me after a couple minutes though. I haven't gotten a chance to play too much with it yet, but I'll let you know how it turns out.

Thanks for the help!

---

### Post by FuturePilot on 2007-04-08
No problem!:)  I think that the GeForce 2 Go can't handle Beryl to well though:(

---

### Post by abaybas on 2007-04-10
I set it up to use xgl and it seems to be mostly stable now. Thanks for that tip.

I know the geforce 2go can't handle some of the fancier effects, but most of what I want runs fine. I get wobbly windows, 3d desktop cube ( no transparency ), expose, simple windows effects. I think that's still impressive for a 5yr old laptop. :)

* Btw: I did notice some slow down with scrolling in firefox though. I checked if smooth scrolling was on, but it's not. Did you notice the same?

Thanks for the help.
Take care.

---

### Post by RedRaider1863 on 2008-06-14
Resurrecting this old thread.  I'm brand new to Ubuntu so please bear with me.  I have an Inspiron 8200 with geforce 2 go, running Hardy.  Is anybody here running Hardy and Compiz Fusion on the same hardware without any problems? I have the nVidia drivers installed using Envy. The color depth in  xorg.conf is set to 24.  powernowd is disabled.  Compiz Fusion is installed.  With desktop effects disabled, it's stable.  When I enable desktop effects, it will freeze randomly.  I especially notice it if I have multiple overlapping windows, usually one of them being Firefox.  I can get some of the cool effects though, before it freezes, like the rotating cube, etc.  I'm not sure what else to try.  Any ideas?

---

### Post by overdrank on 2008-06-14
> **RedRaider1863 said:**
> Resurrecting this old thread.  I'm brand new to Ubuntu so please bear with me.  I have an Inspiron 8200 with geforce 2 go, running Hardy.  Is anybody here running Hardy and Compiz Fusion on the same hardware without any problems? I have the nVidia drivers installed using Envy. The color depth in  xorg.conf is set to 24.  powernowd is disabled.  Compiz Fusion is installed.  With desktop effects disabled, it's stable.  When I enable desktop effects, it will freeze randomly.  I especially notice it if I have multiple overlapping windows, usually one of them being Firefox.  I can get some of the cool effects though, before it freezes, like the rotating cube, etc.  I'm not sure what else to try.  Any ideas?

Hi and welcome, I am assuming this system is a laptop, then you may look into how much memory is being shared with the graphics in the bios. :)

---

### Post by RedRaider1863 on 2008-06-15
> **overdrank said:**
> Hi and welcome, I am assuming this system is a laptop, then you may look into how much memory is being shared with the graphics in the bios. :)

Thanks, I'll look into that.

---

