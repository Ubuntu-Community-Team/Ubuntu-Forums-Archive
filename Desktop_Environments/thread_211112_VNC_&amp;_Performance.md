---
title: "VNC &amp; Performance"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Kurdt on 2006-07-07
Hi :)

This thread is intended to share experiences about vnc (in all its flavours) performance, I have never got the same performance connecting to the same computer within Linux (or FreeBSD) and Windows.

Windows vnc clients (realvnc for example) is always faster, i am talking about the same computer, same conditions (dual boot).

I doubt that you all didn't notice this before, so, what is the workaround chosen ?

Thanks for all comments ;)

---

### Post by Thund3rstruck on 2006-07-07
Can't say I have the same result but then I use windows terminal services and not VNC (but I think they use the same RDP protocol). I terminal service into my W2K Server from both XP and Ubuntu 2.6.15-25-686 and I can't say I have had any differences in performance between the two

---

### Post by Memnoch on 2006-07-09
No its not the same RDP protocol. VNC is a different protocol than RDP. I have experienced the same as the OP. I use RealVNC 4 at work on my windows box to get to my servers and it is much faster than the VNC that Ubuntu comes with. I saw that they were different versions so I went to Synaptic and got the vnc4common and xvnc4viewer packages but then when I tried to connect to an ip, the window that comes up won't let me type in anything. Same thing happens both at home and at work.

So I'm thinking of downloading RealVNC and installing that. Although I would've preferred it as a deb package rather than a regular linux installation.

---

### Post by Kurdt on 2006-07-10
exactly! that is what happens to me, vnc performance over linux is really bad... and RDP too, so, what do you think is happening under the hood?

Thanks for sharing comments ;)

---

### Post by digs on 2006-07-10
Did you install the video driver for the vnc server? It speeds up screen updates a good deal and with ultravnc as server I see negligible difference between a linux, windows, or mac client.

---

### Post by cptnapalm on 2006-07-11
Is it only me or is it sort of daft that a Windows VNC client outperforms Unix when the thing was designed for Unix in the first place?

Of course this is an X thing and, right now, don't get me started on X...

---

### Post by Kurdt on 2006-07-12
> **digs said:**
> Did you install the video driver for the vnc server? It speeds up screen updates a good deal and with ultravnc as server I see negligible difference between a linux, windows, or mac client.

Video driver for the vnc server? well.. i'll have to read about that, thanks

I used UltraVNC as a server too and i did not see any improvement :( 

thanks for all responses...

---

