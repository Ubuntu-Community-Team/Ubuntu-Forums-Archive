---
title: "connecting 2 ubuntu computers with ethernet"
date: 2005-12-05
forum: Desktop Environments
---

### Post by emm721 on 2005-12-05
i have 2 computers, 1 with a massive hard disk and a laptop. when docked, i want my laptop to connect with the big computer with an ethernet cable, just so i dont have to make it into a server, then have to connect it to the internet, etc. are there any programs for this, do i use the terminal, or is it in network or something?

---

### Post by JShadow on 2005-12-05
The purpose is to share files? If so Samba or NFS would do the trick. 

Make sure you use a crossover cable if you are connecting them directly, then configure their IPs to be in the same range, like "192.168.0.1" and "192.168.0.2".

---

### Post by emm721 on 2005-12-05
yeah. i want to share files, but only personally, not like a server but more like streamload.com. and i am a noob, so what exactly is a crossover cable? plus could you give like step-by-step? i assume the samba and nfs is in synaptics, so start from right after there. just connect them?

---

### Post by dcstar on 2005-12-06
[QUOTE=emm721]yeah. i want to share files, but only personally, not like a server but more like streamload.com. and i am a noob, so what exactly is a crossover cable? plus could you give like step-by-step? i assume the samba and nfs is in synaptics, so start from right after there. just connect them?[/QUOTE]
A "crossover" cable is a specially wired network cable to connect two PCs together, rather than have the PCs each connect via a switch/hub.

Some modern network cards are "auto-crossover", so you may be able to connect your equipment with a standard network cable (try it, if the lights come on ok then you have a connection).

If your networking equipment has spare network ports, it would be better to connect both like this (and then you still have 'net access).

---

### Post by emm721 on 2005-12-06
alright, and see i have a thing set up where each computer has wireless, both are connected to the same network, the network has lan/file transfer disabled, and they also have a ethernet port. thats what i want them to connect through. the old computer is like 5-6 years old, so i dont know if it has auto-crossover.

---

