---
title: "Remote access/ login help"
date: 2006-09-28
forum: Desktop Environments
---

### Post by icemallet on 2006-09-28
Hello,
  I have ubuntu on a second computer, which will soon not be hooked to a monitor or anything. I figured out how to do remote access, but my problem is that I can't put in my username and password with the remote accessing program. So my question is how can I get pass the login screen with my remote access program?

---

### Post by scxtt on 2006-09-28
what is your "remote access program" ... ?

---

### Post by icemallet on 2006-09-28
Well the server remote acessing program I am using the one that comes with Ubuntu. Now for the viewer I use either UltraVNC or .NET VNC Viewer.

---

### Post by scxtt on 2006-09-29
the one that "comes with Ubuntu" is vino, which shares your x11 :0 connection AFTER you're logged in ...

your best bet is to ssh into the ubuntu box, start a vncserver connection and use a vncviewer to connect to it ... do a **sudo aptitude install vncserver** on the ubuntu box ...

the only way to get a graphical login from windows --> unix/linux that i know of is via XDMCP and i don't know of (m)any $0 apps for that ... the only one i'm aware of is Exceed, and it's not cheap ...

---

### Post by motin on 2006-10-08
> **scxtt said:**
> the one that "comes with Ubuntu" is vino, which shares your x11 :0 connection AFTER you're logged in ...

your best bet is to ssh into the ubuntu box, start a vncserver connection and use a vncviewer to connect to it ... do a **sudo aptitude install vncserver** on the ubuntu box ...

the only way to get a graphical login from windows --> unix/linux that i know of is via XDMCP and i don't know of (m)any $0 apps for that ... the only one i'm aware of is Exceed, and it's not cheap ...

Here is the approriate guide. You will have "Exceed" functionality with vnc4server:
" HOWTO: Set up VNC server with resumable sessions" - [http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

---

### Post by hyper_ch on 2006-10-09
How to do that with kubntu as there is no /etc/gdm/gmd.conf and I can't find the kdm.conf ?

---

