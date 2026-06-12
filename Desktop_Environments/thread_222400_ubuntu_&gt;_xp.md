---
title: "ubuntu &gt; xp"
date: 2006-07-24
forum: Desktop Environments
---

### Post by selfmade on 2006-07-24
ive looked through a lot of the posts on the subject, thought im sure i didnt hit all of them. my xp machine is connected to the internet via my neighbor's wireless network, while my ubuntu machine is connected to the cable.i downloaded rdesktop and have played with the terminal server client, but cant seem to get it going.
is it still possible to access the xp machine from the linus machine in this situation?

---

### Post by encompass on 2006-07-25
yes, but not recommended, you have to have a pretty good reason.
Because both are in completely different networks, it would be rather hard to connect to the other computer without alot of setup.
Windows has tools to connect to it remotely but I haven't the foggiest idea how.  Ask Microsoft that :P.
As for the otherway arround... connecting to your linux computer from windows... that is alot easier.
So I wouldn't recommend it for security reasons.'

---

### Post by dtfinch on 2006-07-25
If using "Terminal Server Client", and you have Remote Desktop enabled on the XP machine (assuming it's Pro), make sure you choose RDPv5 for the protocol. If it's XP Home, install a VNC server like tightvnc or untravnc.

Have you thought about setting up a home network? Going out to the internet, back to your neighbor's connection, and over their wireless network to get to your 2nd desktop sounds kind of inefficient.

---

