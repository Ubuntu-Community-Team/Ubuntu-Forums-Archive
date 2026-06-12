---
title: "adesklets"
date: 2006-11-25
forum: Desktop Environments
---

### Post by robin_0.8.2 on 2006-11-25
HI

am trying to install adesklets. when I type ./configure i get this at the end of the process:

configure: error: cannot find Python include path

without this i cannot compile
any clues?

cheers
R0.8.2

---

### Post by taurus on 2006-11-25
Do you have python on your system and I believe adesklet is available from repos?

```
sudo aptitude update
sudo aptitude install adesklets
```

---

### Post by robin_0.8.2 on 2006-11-25
yes i got it from the repo. now i wanted to install this adesklet called weather. it's a .py file. So i typed python weather.py asks me if i wanna register or test and then after I typed 'adesklets weather'.

Thinks about it for a while but nothing happens..

can u help?

---

### Post by taurus on 2006-11-25
Once you registered the applet, I don't even think you have to type the name of it anymore.  Just adesklets by itself should do it...

---

### Post by racoq on 2006-11-27
think my guide will anwser all your questions


[http://www.ubuntuforums.org/showthread.php?t=183709](http://www.ubuntuforums.org/showthread.php?t=183709)

---

### Post by robin_0.8.2 on 2006-11-27
thanx a mill

---

### Post by robin_0.8.2 on 2006-11-27
i post you what i get after typing adesklets -i:

KeyError: 'TkGUI'

something's wrong with tk something
can you help?

---

### Post by ahh_dee on 2006-12-26
Hey man your not alone i am getting the same problem.  I am trying to install adesklets 0.6.1 and i am getting a python error when i type in ./configure.  The synaptic one was out of date and I have been getting problems registering my desklets

---

