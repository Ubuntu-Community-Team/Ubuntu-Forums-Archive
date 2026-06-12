---
title: "KDE won't work"
date: 2010-05-07
forum: Desktop Environments
---

### Post by clayman1000x on 2010-05-07
[I]
sudo apt-get install kubuntu-desktop 
[/I]
                           

Ok, I tried using this and it seemed to work installing the  desktop, however when I try to load the desktop I can hear the boot up  sound but get no desktop, I have to con alt del to restart ubuntu. What  could be my problem here? I also had this problem before reinstalling  KDE.

---

### Post by darkenvy6 on 2010-05-07
can you get to the TTY? Oh I remember having this problem a while ago and had to work with the upstart, I'm rather new to that so I don't really remember what I did. I hope this helps

---

### Post by Zorael on 2010-05-08
(I'm assuming this is in lucid.)

Do you get a mouse cursor and a black screen?

There have been a few threads recently where people for some reason ended up missing **plasma-desktop** after having tried to install KDE or Kubuntu.

Can you hit Alt+F2 when at that black screen and start a terminal?
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
$ sudo aptitude install plasma-desktop -f
```
If you don't have a net connection at this point it's a bit more troublesome. See if you can get a network management plasma widget to pop up by doing the following. (needs lucid)
```
$ plasmoidviewer networkmanagement &
```
If you can get a working net connection using that, try the first commands again.

Then log out and back in (Alt+F2 and '**logout**'), or just start plasma manually, from a run box (Alt+F2, '**plasma-desktop**') or that terminal.
```
$ plasma-desktop
```

---

### Post by kio_http on 2010-05-08
> **clayman1000x said:**
> [I]
sudo apt-get install kubuntu-desktop 
[/I]
                           

Ok, I tried using this and it seemed to work installing the  desktop, however when I try to load the desktop I can hear the boot up  sound but get no desktop, I have to con alt del to restart ubuntu. What  could be my problem here? I also had this problem before reinstalling  KDE.

Did you set KDM or GDM as your login manager?

---

