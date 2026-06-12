---
title: "Secure Remote Desktop through Windows?"
date: 2005-12-31
forum: General Help
---

### Post by anaoum on 2005-12-31
Hello,

I was wondering if there is a way to securely access my ubuntu machine through remote desktop (or any other alternative) using a program on a seperate windows machine?
I have also heard that you can ssh into the machine, then start gnome, but i am unsure if it works. If it does could someone please explain...

Thanks,

---

### Post by budluva04 on 2005-12-31
setup a VNC server on your ubuntu machine, then get a VNC client on your windows or other linux machines, TightVNC is good, it has both server/client packages

apt-get install tightvncserver

[www.tightvnc.com](www.tightvnc.com) for the windows client files

---

### Post by anaoum on 2005-12-31
Are you sure this is secure? I have read a lot of bad stuff about vnc.

---

### Post by Suger on 2005-12-31
What you are looking for, then, is Cygwin, a Linux emulator for Windows.

---

### Post by anaoum on 2005-12-31
Cygwin is a linux emulator for windows, this is not want im looking for. I need to be able to remotely access my ubuntu pc through a windows pc, securely.

---

### Post by stack445 on 2005-12-31
You could enable X11 fowarding through ssh, or used freenx nomachine stuff. 

[http://www.nomachine.com]("http://www.nomachine.com")

---

### Post by joe_d on 2006-01-01
[QUOTE=budluva04]setup a VNC server on your ubuntu machine, then get a VNC client on your windows or other linux machines, TightVNC is good, it has both server/client packages

apt-get install tightvncserver

[www.tightvnc.com](www.tightvnc.com) for the windows client files[/QUOTE]


What are your sources pointing to? 
I get:
root@wombat:/usr/src/cvc_linux-rh-gcc3-3.3# apt-get install tightvncserver
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package tightvncserver

---

### Post by steve.horsley on 2006-01-01
1: Start Synaptic: System->Administration->Synaptic Package Manager
2: Add Multiverse and Universe repos: Settings->Repositories, +Add, check them all, OK, OK
3: Search for VNC, mark and install the things you want

---

### Post by joe_d on 2006-01-01
Thanks very much!  That did the trick.

---

