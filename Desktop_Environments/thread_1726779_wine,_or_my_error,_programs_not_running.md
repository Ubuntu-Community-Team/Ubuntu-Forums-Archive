---
title: "wine, or my error, programs not running"
date: 2011-04-11
forum: Desktop Environments
---

### Post by amerinde on 2011-04-11
i got a a problem, i used to run wine and a windows chat program. I got away from linux for a while, but now am back, but the same program i used to run, now gives and error.. to check my internet connection. <urlopen error [Errno 5] Access denided> I gave the program the permission to run, but what am i missing?

---

### Post by amerinde on 2011-04-12
oh my... can no one help?

i know, leave the windows aps and use linux, but some of the stuff isnt available for linux..

---

### Post by 3Miro on 2011-04-12
Which version of Ubuntu (i.e. 10.04, 10.10).

Which version of wine (1.1, 1.2, 1.3 ..., is it release or alpha, you can hit Alt+F2 then type "winecfg" and it will tell you). Beta versions update often and sometimes break things from one release to the next. On the other hand betas have more features and generally run more stuff.

What is the chat program? Have they released a new version of the chat program, if so, they may be blocking old clients.

Access denied is related either to the Ubuntu firewall (unlikely) or the server on the other end (more likely).

Please provide the above information so we can help you.

---

### Post by amerinde on 2011-04-13
im using wine 1.0.1... the chat program is IMVU. they have had many updates. oh, i am using ubuntu 10.10

---

### Post by 3Miro on 2011-04-13
Something isn't adding up. 10.10 comes with wine 1.2 (stable) and 1.3 (unstable). Also, IMVU seems to be in rather active development, you may have to update that.

IMVU also requires 3D acceleration, what is your video card. Nvidia is your best bet, Intel and ATI are not very stable.

Try going to the Software Center and see which version of wine you have. Try installing wine 1.2 (stable). If you don't have any other wine applications, you can try to rename your .wine folder (use Home -> Places and then hit Ctr + H) then reinstall the latest version of IMVU again.

---

### Post by amerinde on 2011-04-15
this is a fresh install of Ubuntu 10.10. when i downloaded IMVU, i had to install wine, only option i had from package manager was 1.0. My graphic card is definite 3D, Nvidia GeForce GTX 480. I will look for a newer version of wine.

---

### Post by amerinde on 2011-04-15
ok, this is messed up, i found wine 1.2........ installed and reinstalled IMVU, it now runs, but i cant see it, but i hear the sounds from IMVU and the icon in the upper right. Do i need to change the permissions??

---

### Post by 3Miro on 2011-04-15
> **amerinde said:**
> ok, this is messed up,


Yep, that is wine. Often times you have to spend a great deal of effort to make things work.

> 
 i found wine 1.2........ installed and reinstalled IMVU, it now runs, but i cant see it, but i hear the sounds from IMVU and the icon in the upper right. Do i need to change the permissions??

Is t minimized to tray? Does it appear if you press Alt+Tab? 

Check this forum. WineHQ is usually the right place for wine related problems. They can help with application specific issues. Apparently you have to edit some "registry" keys. To do that, open a terminal (Apps -> Access -> Terminal) and type:
```
wine regedit
```

Here is the WineHQ entry:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21020](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21020)

---

### Post by amerinde on 2011-04-16
no, IMVU is not minimized. alt.+tab only shows firefox. But the IMVU icon shows on the indicator bar. When i look at system monitor to kill the process, it shows IMVU as sleeping.

---

### Post by 3Miro on 2011-04-16
> **amerinde said:**
> no, IMVU is not minimized. alt.+tab only shows firefox. But the IMVU icon shows on the indicator bar. When i look at system monitor to kill the process, it shows IMVU as sleeping.

If you click on the IMVU icon, doesn't it bring up something.

---

### Post by amerinde on 2011-04-17
when i click the icon, it does nothing. just hovering over it it shows IMVU. i have the imvi prograqm started now, i hear the sounds from imvu, but cant see it. could it be something with my dual monitors? it runs fine on this pc under windows.

---

