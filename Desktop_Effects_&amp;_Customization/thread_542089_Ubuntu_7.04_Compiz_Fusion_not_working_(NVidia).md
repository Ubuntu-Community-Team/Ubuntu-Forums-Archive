---
title: "Ubuntu 7.04 Compiz Fusion not working (NVidia)"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by phophe on 2007-09-03
Hello everybody. I am new in the forum and in ubuntu. 
I have installed Ubuntu 7.04 and use the desktop effects that come with it. So I thought that compiz fusion should work because desktop effects worked correctly, so I followed the guide of this forum about the best way to install compiz fusion.
All the process of installation was correct, but when finally I typed compiz --replace in the terminal, I got the following output:
[INDENT]
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'gotovp'

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5208): Wnck-WARNING **: Unhandled action type (nil)[/INDENT]

Any help will be appreciated, thanks in advance. If it helps I can say that the commands glxgears and glxinfo work and direct rendering status is yes.
Let me know if I have to post some file such as xorg.conf or more data.
My specs are Laptop P4 2.6GHz 512MB RAM, NVidia Geforce FX Go5600 with driver 100.14.11

---

### Post by Phurious on 2007-09-03
I was getting a very similar error when trying to get Compiz running on my box.  This post [http://ubuntuforums.org/showthread.php?t=533476]("http://ubuntuforums.org/showthread.php?t=533476") finally got me up and running.  Hope it helps!

---

### Post by phophe on 2007-09-04
Thanks for the reply. I finally managed to get compiz fusion working in the followay way.
I completely removed it and reinstalled it following the guide "the best way to install... " but this time in the configuration of compiz leave the gcon instead of flat file, and in windows decorator selected the default any instead of gtk-window-decorator.
Now everything works well except and extrange isue, if I am using compiz fusion and I try to shutdown the computer, then the computer hangs and I have to shut down the computer switching the power off button for five seconds.
But if I type metacity --replace before turning off the computer then the computer switchs off correctly.
Thanks in advance.

---

### Post by Inxsible on 2007-09-04
did you use Amaranth's repos or Trevinos ?

I use compiz and i dont have to switch to metacity before shutting down or anything.

It could be because you use gconf as backend. I use flat file backend and everything works for me

---

### Post by Bigdeath on 2007-09-04
If I had beryl SVN befrore I installed this would it cause trouble? On my beryl manager I can switch to compiz now but it loads for a split second, then goes back to what looks like metacity, although compiz is still selcted as the windows manager.

---

### Post by Inxsible on 2007-09-04
As long as Beryl is not running, you should be good.

But if you have Beryl in your startup and you run Compiz Fusion...it wreaks havoc as attested by quite a few people :)

---

### Post by Bigdeath on 2007-09-04
Now this is weird. I had compiz running perfectly with emerald and everything all day. And earlier it just stopped working. I get the unable to load ccp plugin error and now I have the no borders problem again.

---

