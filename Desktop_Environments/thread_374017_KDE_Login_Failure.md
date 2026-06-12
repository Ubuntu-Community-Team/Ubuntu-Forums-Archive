---
title: "KDE Login Failure"
date: 2007-03-01
forum: Desktop Environments
---

### Post by Falandar on 2007-03-01
Hey, first time posting, long time reading.  I've been using Ubuntu for the past few months with great success.  I've hit the occasional pitfall every now and then, but so far I've been able to read the forums and use the wealth of knowledge contained within.  Unfortunately, I've run into a problem that I did not see while searching the forums.  If anyone knows how to solve it, or whether it has already been asked just let me know.

Basically, I set up another Ubuntu server in my house to run as a webserver.  I setup VNC and KDE last night.  I was tooling around for a bit and then decided to install the 1957901 updates that needed to install.  I ran it overnight, and then reboot it in the morning.  When I came home, I started the server up and came to the login screen.  

When I type my username/password into the login prompt, the screen goes grey for a second, the little wheely pops up and spins, and then it spits me back out to the login screen again.  If I ctrl+alt+f1, I can login fine.  If I try to do startx, I get some failures about a wacom driver, and then a few lines about font problems.  So I think something is up with my x11 for my KDE.  I've tried using sudo dpkg-reconfigure xserver-xorg to get a new x11 config file created, but I'm still running into the same problem.  Does anyone have any ideas as to what I should do next? Thanks for your help!

-Sean-

---

### Post by shareMenaPeace on 2007-03-02
DO you have discspace left?

check with 
```
df -h
```

---

