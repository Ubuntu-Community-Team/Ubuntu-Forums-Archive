---
title: "System sends and recieves data every 20sec, with no progs running, what' s going on?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by aaron on 2006-07-19
I noticed my harddrives were reading/writing data every few seconds, even when no programs were left open. On checking the system monitor everything said it was 'sleeping' except for 'gnome-system-monitor' (of course) :)

Anyway, under the resources tab something odd shows up in the network history. Every 20 seconds the computer sends 23 bytes of data, and then recieves 4.5 KiB of data. The send and recieve are offset from each other by about 5 seconds. 

Rebooting doesn't change this network activity. 

Is this something that I should be worried about? Or should I look into stronger security settings?

P.S. I'm using a wireless lan setup, and there are two windows xp boxes on the network. Dunno if that would have something to do with it?

---

### Post by goobers on 2006-07-19
I would imagine it is just sending data to maintain the connection, don't hold me to that though

---

### Post by nicbink on 2006-07-19
install ethereal and snoop the packets.

---

