---
title: "gsettings is restarting X/unity on changes"
date: 2015-05-18
forum: Desktop Environments
---

### Post by aqueafex on 2015-05-18
ubuntu 14.04 LTS

Must be some new update but now all gsettings changes are crashing and restarting X/unity

example:
```

gsettings set org.gnome.desktop.interface font-name 'Ubuntu 15'
gsettings reset org.gnome.desktop.interface font-name

```


it seems that on changing a value through gsettings -- unity crashes and restarts

This makes gsettings completely unusable! 

Can anybody confirm?

---

### Post by monkeybrain20122 on 2015-05-18
No problem here using either the command line or dconf-editor.

---

### Post by CantankRus on 2015-05-19
See similar to **aqueafex**.
Running the first command sends me to the greeter.

Compiz also seems to load differently with a reboot to logging out and back in.
From a logout then login my edge triggers don't work.
Used to run "setsid unity" to reload and edge triggers would work again but now the command logs me out.
Have to run "compiz --replace" which doesn't log me out.

---

### Post by aqueafex on 2015-05-19
Something broke and it's very recent. Must be a change they pushed out within the last 2 weeks. Everything was fine before.

---

### Post by aqueafex on 2015-05-22
Where can I report this bug so something is actually done about it?

---

### Post by deadflowr on 2015-05-22
I would guess report the bug against dconf-gsettings-backend.
Seems like a likely candidate...
Ubuntu has an in-built bug reporting tool called apport.
Learn more from here
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by mc4man on 2015-05-24
I also cannot cause this to happen, gsettings & or dconf write commands are fine (scr. shows your example in single terminal., fully updated to 14.04.2
If still affected I'd try setting up a new user & see if that user can use gsettings/dconf successfully

---

### Post by aqueafex on 2015-05-26
You must be lucky mc4man, just tried it with a new user and the same thing happens.

I'm on fully updated:

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

Linux 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


So we're 2/4 so far on this thread for people affected.

---

### Post by jdorenbush on 2015-07-30
This is happening to me too.

Ubuntu 14.04

---

### Post by mohammadanwarshah on 2015-08-11
I am experiencing the same issue. Every time i change font, this crash happens. This is soo annoying

---

