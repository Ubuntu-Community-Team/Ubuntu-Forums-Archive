---
title: "Need Terminal Bell to Work"
date: 2012-06-20
forum: Desktop Environments
---

### Post by ubuntalot on 2012-06-20
I just installed ubuntu 12.04 with Unity and I have an application I use which requires the terminal bell to work in order for me to hear certain alerts.
How do I do this?

---

### Post by kanikilu on 2012-06-20
This thread has some useful suggestions:

[http://superuser.com/questions/22767/enable-system-beep-in-ubuntu](http://superuser.com/questions/22767/enable-system-beep-in-ubuntu)

By the way, keep in mind that the PC speaker kernel module is blacklisted by default. The first thing I'd do is re-enable it...

---

### Post by ubuntalot on 2012-06-20
Well in KDE the bell goes through the external speakers.  Is it possible to direct Unity to send the bell to the external speakers?

---

### Post by ubuntalot on 2012-06-20
> **kanikilu said:**
> This thread has some useful suggestions:

[http://superuser.com/questions/22767/enable-system-beep-in-ubuntu](http://superuser.com/questions/22767/enable-system-beep-in-ubuntu)

By the way, keep in mind that the PC speaker kernel module is blacklisted by default. The first thing I'd do is re-enable it...

I found that post before I opened this thread :( none of that stuff worked for me (it is 2 years old).
I will not be able to use ubuntu without this feature.
I am a System Administrator and I open an ssh to another linux server and run a program which monitors various processes and beeps if a problem is found so that I can turn my attention to it.  I don't want to re-write the program, I just need the terminal to beep as it should when a \a is sent.

---

### Post by dommelen on 2013-01-06
The following link actually works!  :)

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_12.04_%28Precise_Pangolin%29_on_a_ThinkPad_X220](http://www.thinkwiki.org/wiki/Installing_Ubuntu_12.04_%28Precise_Pangolin%29_on_a_ThinkPad_X220)

Anyone who does some programming needs a terminal bell.

---

