---
title: "remotely control computer on LAN?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by bionnaki on 2006-08-25
what are the steps for remotely controlling one computer connected wirelessly via router with other computer on the network? Both are running ubuntu.

thanks!

---

### Post by amo-ej1 on 2006-08-25
there are various paths to try you could:
a) use ssh to get a remote command line (which is secure)
b) you could use remote X or vnc alikes (which are mainly insecure, but you can tunnel them inside ssh) to get your remote desktop at your current workstation
c) you could use ssh forwarding to get a single remote X application on your current desktop (first run xhost + (to allow access for remote servers to connect), then connect to the machine ssh -X user@host enter you password and start your X application, the -X flag tells ssh to enable X forwarding, this gets encrypted and is secure, altough the xhost + could be done better).

hope this helps, but defining what you exactly want to do will get your further

---

### Post by bionnaki on 2006-08-27
basiscally, I'd like to be able to turn off (or simple reduce the volume) of my roommates amarok. I'd also like to be able to remotely administer the computer - you know, updates etc. I want to control the computer from mine.

---

