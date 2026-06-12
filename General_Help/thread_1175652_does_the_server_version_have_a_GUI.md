---
title: "does the server version have a GUI?"
date: 2009-06-01
forum: General Help
---

### Post by StarThorn1 on 2009-06-01
If the server version has a GUI then what command do i need to type to make it run?

---

### Post by abn91c on 2009-06-01
> **StarThorn1 said:**
> If the server version has a GUI then what command do i need to type to make it run?
no, you have to install from the CLI: sudo apt-get install ubuntu-desktop

---

### Post by StarThorn1 on 2009-06-01
> **abn91c said:**
> no, you have to install from the CLI: sudo apt-get install ubuntu-desktop
I tells me "could'nt find package ubuntu-desktop

---

### Post by abn91c on 2009-06-01
> **StarThorn1 said:**
> I tells me "could'nt find package ubuntu-desktop
log in to the server first make sure you are connected to the network, if not[COLOR="Blue"] sudo dhclient eth0[/COLOR], then run[COLOR="Red"] sudo apt-get install ubuntu-desktop[/COLOR]
after it installs type **startx** at the prompt

---

### Post by netpro25 on 2009-06-01
You may need to run sudo apt-get update first

---

### Post by StarThorn1 on 2009-06-01
> **abn91c said:**
> log in to the server first make sure you are connected to the network, if not[COLOR="Blue"] sudo dhclient eth0[/COLOR], then run[COLOR="Red"] sudo apt-get install ubuntu-desktop[/COLOR]
after it installs type **startx** at the prompt

Still the same thing. When I did the dchlient eth0 it said "chmod: failed to get attributes etc/resolve.conf

---

### Post by binbash on 2009-06-01
It does not have a gui, and do not install a gui to a server.

---

### Post by StarThorn1 on 2009-06-01
> **netpro25 said:**
> You may need to run sudo apt-get update first


This worked, thanks

---

### Post by Keatonguy on 2009-06-01
Nope, the server installation is just the barest of bare bones. It strips out all the GUI to minimize system resource usage and potential security flaws. You can install the ubuntu-desktop package, but I'm pretty sure you may as well just install using the desktop CD at that point...

---

### Post by munky99999 on 2009-06-01
Ctrl Alt F8 or one of those keys will actually switch around and basically turn on/off the desktop.

Ctrl Alt F7 will return you back to the xwindows. Which then in of itself lets you turn xwindows off and speed the performance up :)

So yes in a way you can just use the desktop version. However the iso wont have the lamp and all those apps ready to install. Though yes you can just grab them from synaptic.

---

### Post by Iowan on 2009-06-01
May as well toss [this]("https://help.ubuntu.com/community/ServerGUI") one out.

---

