---
title: "Remote desktop in 9.04 release candidate"
date: 2009-04-17
forum: Desktop Environments
---

### Post by mifi on 2009-04-17
I installed a fresh 9.04 rel.cand. and went to preferences/remote desktop and checked:

allow other users to view my desktop
allow other users to control my desktop
require password
automatically configure network to listen for connections

Then I walked to a PC running XP and tightvnc and connected to my machine. All went well: I was asked for the password and after entering that I got the remote desktop.

However, if I move the mouse in the client, this is not reflected on my screen. On the remote machine the pointer is moving and I can click as well, but I do not get to see all that in my client side screen.

Anything I am overlooking or is this a bug in 9.04?

m

---

### Post by gitti on 2009-04-23
I have the same problem with the 9.04 final release.

Have you solved?

---

### Post by mifi on 2009-04-23
> **gitti said:**
> 
Have you solved?
It is not a real solution, but I installed 8.10.

m

---

### Post by gitti on 2009-04-23
> **mifi said:**
> It is not a real solution, but I installed 8.10.

m

Today I installed 9.04, I don't want to go back.

---

### Post by gitti on 2009-04-24
We solved here disabling compiz.

[http://ubuntuforums.org/showthread.php?p=7132508](http://ubuntuforums.org/showthread.php?p=7132508)

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

### Post by linuxgnubee on 2009-08-24
I, too, gitti just upgraded to 9.04 (on my tower PC) in order to take advantage of remote desktop, using 9.04 on my Netbook. I like everything same-same, ya know?

I added Gnome-RDC to my Netbook as well as Terminal Services Client, thru Applications > Add/Remove ... thinking it functions much like RDC on the Windows side. Am I correct in assuming this? It should, right, Ubuntu to Ubuntu.

I configured the Remote Desktop Viewer on my tower PC (allow other users to view my desktop, allow other users to control my desktop, require password, automatically configure network to listen for connections) and then attempted to connect from the Netbook using Gnome-RDC and no go. Now, 1) I tried this wirelessly from the Netbook to the tower (the tower being connected to the router via ethernet) - so perhaps there lies the issue or 2) I used the wrong hostname - should it be name.local[colon][colon]portNumber (darn smileys pick up on colon'p' and put a smiley in my text, so I have to write it out longhand!) or could I have used the ip address itself?  Hmmm ...

Also, on the Windows XP side, why must I use something like TightVNC or RealVNC? The built-in RDC won't provide connectivity?

Thanks for any quidance, folks.

---

### Post by gitti on 2009-08-25
I don't understand if you want to connect locally or remotely.

---

