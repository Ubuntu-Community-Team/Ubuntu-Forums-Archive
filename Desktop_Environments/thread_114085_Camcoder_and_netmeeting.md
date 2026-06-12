---
title: "Camcoder and netmeeting"
date: 2006-01-07
forum: Desktop Environments
---

### Post by damotor on 2006-01-07
Hello.
I'd like to use ubuntu to talk by netmeeting with my JVC gr-d240e camcoder but I was unable to do it with mercury and amsn. The problem is that this programs seems to only acept v4l compatible devices and mine is a firewired one. The camcoder works perfect with kino and also in windows. Can u help me? please.

Thanks.

---

### Post by damotor on 2006-01-09
Hi again.
While I was searching for a solution I found coriander, wich didn't worked with my camcorder and vloopback. Anyone used vloopback or any other software to convert raw1394 to v4l?

Thank u.

---

### Post by leech on 2006-01-09
Yes, Gnome meeting WILL work with the firewire stuff.  You'll want to install the libpt-plugins packages.  I think the specific one you want is the libpt-plugins-avc or it's the dc.  One of those two...

Either way, it does work. I've gotten it to work on my laptop with the firewire.

Leech

---

### Post by chele on 2006-01-09
**libpt-plugins-avc** is the package that works for me with gnomemeeting. I then put the firewire connected camcorder in it's "camera" mode, and away it goes.

One thing I have noticed is that the camcorder shuts itself off after a short period of time. I have not found how to disable this, either through software or the camcorder itself. I am using a Sharp Viewcam.

The same also works with the latest cvs of Gnomemeeting. For version 2.00, Gnomemeeting is being renamed to ekiga, which should out real soon now. [http://blog.gnomemeeting.net/]("http://blog.gnomemeeting.net/")

---

### Post by andrewsawyer on 2006-01-09
I've had the same problem - friends and family in the UK that I want to keep in touch with while I'm in Australia.  I've got a Sony Handycam, and unfortunately the best/only way that I've found to do it so far was to install VMWare and stick WinXP in it along with Skype 2 Beta and MSN Messenger.  I just have this loaded up on my computer all the time, and use it as my 'contact' window.

On the plus side, I also get to use VoIP Cheap that gives me free calls to landlines, but is only compatible through Windows.

---

