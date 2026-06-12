---
title: "Best way to remote access into desktop. VNC?"
date: 2009-02-05
forum: General Help
---

### Post by ensnare on 2009-02-05
Hi -- I'm about to install VNC on my linux box but I just want to make sure that this is the best option in terms of speed and graphics quality for a remote session to my desktop.  Are there any other recommended programs / solutions?  I'm trying to connect to my desktop from my laptop while on the road.   Thanks in advance for any input / advice.

---

### Post by yther on 2009-02-05
I used to do exactly that, minus the laptop, using a little tool kit (PuTTY and a TightVNC client) I burned onto a mini-CD.  Take a few minutes and work out how to set up **sshd**; using that, you can make a "tunnel" to your system that is encrypted.  VNC provides basically zero security, so you'll want to encrypt it for safety.

Using the default "WAN" settings (IIRC), performance over the Internet was quite adequate with a 1024x768 desktop.

---

