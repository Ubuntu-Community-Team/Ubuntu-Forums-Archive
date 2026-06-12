---
title: "IS it possible to remotly controll my Windows PC"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Sir_Sid on 2006-09-15
I use Ultra VNC to remotely acess my PC from my laptop. Well im starting to switch over to linux and I need a way to acess my PC still. Is there a remote desktop or other VNC like program which can work across operating systems?

---

### Post by artinla on 2006-09-15
VNC is cross platform.. I use it both ways.

Just install the VNC server on the windows box.

I use realvnc.

---

### Post by jwest21 on 2006-09-16
I recently had to reinstall ubuntu on my computer and I lost the remote desktop program that i had previously installed.  I'm hoping someone can help me remeber what program it was because it worked great.

Here's a description of what I remember:
It was not a vnc program.
It used windows remote access on the windows computer, so nothing was installed on that computer.
The login screen looked very similar to the windows remote desktop panel but had the linux penguin on top.

Any suggestions would be great.

Oh, and as a suggestion to this thread, I use xvncviewer without any problems.  The only thing that puzzled me at first was the scrolling of the server desktop...left click to scroll down/right, right click for up/left.

---

### Post by goombah88 on 2006-09-16
you might be thinking of rdesktop.  i use it at home to control my windows server (desktop) from my kubuntu laptop.  works great.

---

### Post by mgmiller on 2006-09-16
I routinely run my work computer (xp pro) from my home machine (Ubuntu 6.06)  I have the stock windows remote desktop enabled on the work machine and from the  Ubuntu box I use Applications > Internet > terminal server client.  You want to configure it for your windows box, so select the RDPv5 protocol.  For Computer:, just enter the ip address of the computer you want to control. Put in the user name you want.  I left the rest of the fields blank.  (On connection to the windows box, you can fill in the user name and password.)  On the display tab, i selected a specified screen size convenient for me and I told it to use specified color depth > High color(16 bit).  I have a fat broadband pipe at both work and home, so this works well for me.  If yours is not as fast, just use a lower color depth.  I left the rest of the tabs at their default settings.  

I use this almost every day and it works great.  The only thing I can't do is transfer files through this connection, but I can start other programs from within the RD session that can transfer files for me.

It's a nice "native" solution for both operating systems.

---

