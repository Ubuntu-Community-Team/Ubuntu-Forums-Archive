---
title: "x11 stops responding"
date: 2010-10-08
forum: Desktop Environments
---

### Post by ryuchao009 on 2010-10-08
Every so often, my display will "crash", for lack of a better word. The screen will show white bars, then it switches to a console for about a half-second, then goes back to showing the bars. The cycle repeats every few seconds. The weird thing is, this only seems to happen under certain circumstances.

I'll be in the middle of an x11 session over ssh as the same user logged into the linux machine (the remote machine is running a gnome display and my computer is rendering a gnome display over ssh simultaneously). Then, putty gives me a message "connection reset by peer". When I try to ping the machine, it receives the packets but reports "Destination host unrechable". When I check the state of the display, it's stuck in the cycle decribed above. The only way I've found to exit this loop was to hold ctrl+alt+delete.

Any ideas on what the problem could be? I'm a casual linux user, but I've never run across an error like this before.

---

### Post by ryuchao009 on 2010-10-23
I decided to use xVNC instead of X11 over SSH since I don't really need to access it outside of my LAN. However, the problem persists. I was in the middle of a file transfer over LAN when my VNC viewer closed on me. Attempts to reconnect resulted in a "Connection refused (10061)" message. I checked the screen only to find it doing it again. The file transfer also cut off.

When the system becomes unresponsive like this, it seems to show a login prompt on tty1. Then it flashes vertical striped bars as if trying to restart x, then it shows the login prompt for a split second and repeats itself.

Anyone have any ideas? This is the first time I've had any severe problem with ubuntu. If it helps any, I'm using Ubuntu Desktop with ndiswrapper installed.

---

