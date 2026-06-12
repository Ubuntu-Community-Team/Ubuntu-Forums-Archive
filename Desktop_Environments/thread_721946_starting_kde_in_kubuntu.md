---
title: "starting kde in kubuntu"
date: 2008-03-11
forum: Desktop Environments
---

### Post by ykongbam on 2008-03-11
i am new to linux..
i installed kubuntu just yeaterday...
when i booted the first time , it opened up the gui i.e. Kde
but when i rebooted...it opened up prompt screen..
can anyone tell me how to start kde again..:confused:
thanx in advanced

---

### Post by bharadwaj on 2008-03-12
try typing 
```
startx
```
that will start the X windows interface which would also start the graphical interface or try hitting ctrl+alt+backspace that would restart KDE session...

---

### Post by ykongbam on 2008-03-12
> Fatal Server Error - No screens found - Fatal IO error 104 (Connection reset by Peer) on x server ":0.0"
by entering

startx

---

### Post by tubasoldier on 2008-03-12
There seems to be an issue with your Xorg configuration file. X11 is the actual graphical environment and its config file is xorg.conf . This file is located in /etc/X11/xorg.conf. 

There are a few ways to fix this issue:
  Think about any changes you made when you first used it then change them back.

or, here is a method which I hear works, although I have never done this one myself:
```
hwd -xa
```
Just type that into the terminal you see.

OR
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
This method will ask you a fair amount of questions. Most defaults work well.

---

### Post by ykongbam on 2008-03-12
1st command says Command not found 

2nd one does not do anything ...

---

