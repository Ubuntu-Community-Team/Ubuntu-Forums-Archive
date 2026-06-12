---
title: "Java web viewer on VNC."
date: 2005-12-28
forum: General Help
---

### Post by cbudden on 2005-12-28
Hello.

If I want to remote connect to my PC via a web browser i can go into it using port 5800.  The PC is windows 98 using RealVNC.  If I try doing the same to ubuntu I get no response.  Whats up?

---

### Post by pharcyde on 2005-12-28
Is the VNC server started on the ubuntu system?  If it is make sure the server you have has java server capabilities and you enable it on port 5800.

---

### Post by cbudden on 2005-12-28
Ok, I installed vncserver but when I run it, I get the error "vncserver: couldn't find "vncpasswd" on your PATH."  I have JRE installed if that helps.

---

### Post by chenel on 2006-01-03
You'll need to run
```
vncpasswd ~/.vnc/passwd
```
That should do it.

I can't remember if the vncserver daemon contains an embedded java applet like the Windows version though... I run x11vnc (tends to be a little faster) instead, and serve TightVNC from an Apache server.

---

### Post by cbudden on 2006-01-03
I tried vncpasswd but it said "vncpasswd" not found.  I found this [http://www.ubuntuforums.org/showthread.php?t=107503](http://www.ubuntuforums.org/showthread.php?t=107503) and used my password i have set up in system-prefs-remote desktop and it worked.  Thanks.

---

### Post by chenel on 2006-01-03
That's where I was going to point you next anyhow :-)

Glad you got it working.

---

