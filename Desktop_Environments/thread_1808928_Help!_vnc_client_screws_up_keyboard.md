---
title: "Help! vnc client screws up keyboard"
date: 2011-07-20
forum: Desktop Environments
---

### Post by greybeard95a on 2011-07-20
Hi all,

Since network file systems seem either broken or slow, I'm trying to get VNC working.

Basically it *does* work.  But the clients I've found so far are very clunky about moving around the screen of the server system, there doesn't seem to be a clean way of exiting the client, and now the keyboard on the system which I ran the client on is completely screwed up.

I need something sane here.

First, how do I get my keyboard working correctly again?

Second, is there a VNC client that's actually any good?

Thanks!

---

### Post by The Cog on 2011-07-23
vinagre is the one I use - it's in the menus as Internet->Remote Desktop Viewer. I've not seen it cause keyboard problems.

If you're controlling a Windows computer, you would be better off using RDP protocol - **sudo apt-get install rdesktop** and then command like **rdesktop 1.2.3.4**.

---

### Post by greybeard95a on 2011-07-23
Thanks, I was following instructions that steered me down another path. I will give this a try.

---

