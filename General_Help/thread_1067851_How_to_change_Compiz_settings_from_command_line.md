---
title: "How to change Compiz settings from command line"
date: 2009-02-12
forum: General Help
---

### Post by etienne@Rofti on 2009-02-12
Hi! I am not a very clever Linux user, and recently broke my desktop environment.

I was playing around with my Compiz window decoration settings, and when attempting to activate some or other form of window blur, I managed to break it. Since then, I only get a black screen whenever I log in, and am forced to use my sister's account on my computer.

Is there a way that I can disable window blur effects from the command line so that I can use my own user account again?

Thanks!
Etienne

---

### Post by etienne@Rofti on 2009-02-12
OK, I managed to fix it, after Googling some more:

1. Start up and, before logging in, choose your session as Failsafe Terminal
2. When in the terminal, type in the following code:
```
sudo apt-get remove --purge compiz-core
```

This will remove Compiz and the configuration that I/you set it to, and you can then type "exit" and log in again normally. Any compositing-reliant programs, such as AWN (in my case) will not start, but that is no problem, as you can just install Compiz again through Synaptic or by typing the following in a command line:

```
sudo apt-get install compiz
```

Just remember to disable the setting as soon as possible that broke your computer, and then tell Compiz to start up and go for it!

---

### Post by tru infini on 2010-02-01
is there any way to achieve this victory without un-installing compiz?

---

### Post by tru infini on 2010-02-01
I found a solution. and here it is for those who like blur windows
login to safe mode. 
hit ctrl+alt+F2
type:username (enter) password (enter)
type:killall compiz (enter) killall compiz.real (enter)
type:sudo reboot now (enter)
type: (sudo password) (enter)
then log on like normal and your compiz settings will be default.

---

