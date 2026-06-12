---
title: "XGL + VNC = Not working"
date: 2006-06-28
forum: Desktop Environments
---

### Post by gurgle on 2006-06-28
I saw an old thread about this, but I dont think it has been solved. Is there a way to VNC/remote into a computer that has XGL running? I know I cant login to the localhost:0 session, but can i create a new session?

Thanks.

---

### Post by gurgle on 2006-06-29
anyone?

---

### Post by scxtt on 2006-06-29
what do you do to create the :0 session? (i think i've seen the code around, but i have no interest in XGL/Compiz, etc. right now so i haven't memorized it) ...

---

### Post by superm1 on 2006-06-30
I noticed the same difficulties.  I run Xgl as a session on :1, and once I connect to VNC, the VNC server crashes.

---

### Post by gurgle on 2006-07-17
anyone found a solution for this yet?

---

### Post by superm1 on 2006-07-17
This is my solution for now.  Any app that I know i'll need remote access to, I launch on a seperate VNC session thats running, started via this script:

startVNC.sh
```
Xvnc :2 -geometry 800x600 -depth 24  -ac -PasswordFile=/home/supermario/.vnc/passwd &
DISPLAY=:2 fbsetroot -solid "FFFFFFF"
DISPLAY=:2 openbox&
DISPLAY=:2 pypanel&

```

Openbox is a very light weight window manager and pypanel is a lightweight running apps manager.

I launch my apps like this then:

```
DISPLAY=:2 azureus &
```

VNC then listens on port 5902 instead.

---

### Post by superm1 on 2006-07-17
> **scxtt said:**
> what do you do to create the :0 session? (i think i've seen the code around, but i have no interest in XGL/Compiz, etc. right now so i haven't memorized it) ...

Are you meaning to create the Xgl :1 session?  You need to make a session entry for gdm/kdm, and then have that session entry point to a script to launch Xgl as a nested X server.  When the Xgl server closes, the script terminates, and the sessions ends.

---

### Post by gurgle on 2006-07-17
id like to have my xgl session by :0 

I vnc into my machine now with <hostname>:1

hope that helps.

---

### Post by superm1 on 2006-07-17
> **gurgle said:**
> id like to have my xgl session by :0 

I vnc into my machine now with <hostname>:1

hope that helps.

Well Xgl as :0 means that it is the only X server running.  This has some inherent problems in that you lose GL & Xv acceleration for all apps.  Look for any howtos on compiz.net that don't describe xgl as a session.  VNC can be started via a script similar to what I previously posted.

I personally recommend running Xgl as a session on :1 for the simple reason that you can still launch accelerated apps on :0.
This is the thread I posted indicating how to do that.
[http://www.compiz.net/viewtopic.php?id=1623&p=1](http://www.compiz.net/viewtopic.php?id=1623&p=1)

---

### Post by saracen on 2006-08-06
I had vnc working fine but then after installing xgl on the VNC server side, it stopped working.  I start xgl on the server by modifying the /etc/gdm.conf-custom file.  What exactly do I have to do to get my vnc connection working again?  I'm not sure what everyone means when they're talking about sessions...

---

### Post by walovaton on 2006-09-13
I have the same problem and this situation is very bad, I just want to see my current and only XGL (or AIGLX) session remotely using VNC.  What are the reasons for it not to work properly?  I don't know if XGL developers are aware of this problem, though.

Every time I configure vino in Gnome it crashes whenever I try to open a VNC connection.

Is there a way to make XGL and Vino play together nicely?

---

