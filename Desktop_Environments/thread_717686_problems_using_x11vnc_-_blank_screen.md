---
title: "problems using x11vnc - blank screen"
date: 2008-03-07
forum: Desktop Environments
---

### Post by chrisworton on 2008-03-07
hello,

This is my first time posting and im relatively new to linux so please be kind!

Ive looked wverywhere and kept posting on here till last.
I hvae gutsy with x11vnc installed and im having a few problems. When i try to connect to my PC from a windows box i can connect and type my password but then i just get a blank black screen. Im thinking its something to do with power management as when i do a fresh restart i can connect fine however if i leave it a while then connect to it, i get a blacnk screen again. ive disabled the screensaver and turned "blank screen" to "never" in power management but that doesnt seem to make any difference. 

Also, I'm trying to make x11vnc start before login with no success. I currently have set an account to autologin on startup and added vnc to sessions. 

id like to try completely disabling the screen blanking as it still seems to do it but im not sure how. 

Thanks in advance for your comments..

Chris.

---

### Post by muchadhesion on 2008-06-28
I have exactly the same problem.

I'm using XUbuntu 8.04

Did you find a resolution?

Is there an alternative to X11VNC that works with Ubuntu?

---

### Post by krunge on 2008-06-28
> **muchadhesion said:**
> I have exactly the same problem.

I'm using XUbuntu 8.04

Did you find a resolution?

Is there an alternative to X11VNC that works with Ubuntu?
Maybe try this x11vnc option: ```
-noxdamage
```

---

### Post by muchadhesion on 2008-07-07
I've been running with the --noxdamage option for a few days now, and all seems much more stable.

Many thanks for the suggestion!

---

