---
title: "help Ubuntu has faked up again"
date: 2008-03-16
forum: Desktop Environments
---

### Post by Acunga on 2008-03-16
Help Ubutnu is down again.It starts in non-graphical environment because I have pressed cntr alt dell as I have read it adjust the monitor brightness, so it went in nongraphical env.I press after taht cntr alt dell and now it always starts in this environment, pls help
I write from the windows partition

---

### Post by tgalati4 on 2008-03-16
If you hit Control-Alt-Delete, then that usually invokes an immediate shutdown.  If you hit Control-Alt-Backspace then that will shut down the graphical environment and dump you to either a terminal or to the login screen.

If you are at a terminal in Linux then issue the command:

>sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by ghost_ryder35 on 2008-03-16
startx

---

### Post by steveneddy on 2008-03-16
> **Acunga said:**
> Help Ubutnu is down again.It starts in non-graphical environment because I have pressed cntr alt dell as I have read it adjust the monitor brightness, so it went in nongraphical env.I press after taht cntr alt dell and now it always starts in this environment, pls help
I write from the windows partition

Please write in plain English. I don't fully understand what you are asking.

---

### Post by kellemes on 2008-03-16
First try "startx¨
If that doesn't work try "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by Acunga on 2008-03-16
sudo dpkg-reconfigure -phigh xserver-xorg
this turned the videoscreen on.I really need to read about this OS, but it's a whole new world and so much windwos users don't know...nvm, tx10000 for help, 
do you knwo how safely to disable my touchpad?

---

### Post by steveneddy on 2008-03-16
Your best bet is to [go here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy").

---

### Post by steveneddy on 2008-03-16
> **Acunga said:**
> 
do you knwo how safely to disable my touchpad?

 knwo - know?

Did you search the forums?

I did and [came up with this]("http://ubuntuforums.org/showthread.php?t=722141&highlight=disable+touchpad").

---

