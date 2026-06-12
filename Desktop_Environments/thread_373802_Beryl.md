---
title: "Beryl"
date: 2007-03-01
forum: Desktop Environments
---

### Post by nerds in parties on 2007-03-01
Hello guys. I am really new to linux and I need some help here.

I have an ATI Radeon Mobility X1600 and have installed the drivers perfectly. i386 and ubuntu 6.10

I have tryied to install Beryl many times and I have done 2 formats for that! I always do something wrong.

So, I would like to give me a good simple way to install Beryl. thanks guys.

---

### Post by 23meg on 2007-03-01
Which instructions did you follow?

If you follow the ones [here]("https://help.ubuntu.com/community/CompositeManager") according to your hardware and Ubuntu version, it should work.

If you have trouble following instructions, you can also use Automatix to install it. I haven't tried this and don't know whether it's reliable; just letting you know.

---

### Post by Astral Abraxas on 2007-03-01
Hi, I just got beryl working a couple hours ago following this tutorial:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

---

### Post by nerds in parties on 2007-03-01
I installed it but still look what I get when I type "beryl"

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extensio

---

### Post by Astral Abraxas on 2007-03-01
sudo apt-get libxcomposite1

o.0, thats what I did when it complained to me about a composite, but it messed up gnome so bad that it couldnt start up the desktop and I had to remove it by starting up in failsafe terminal.

---

