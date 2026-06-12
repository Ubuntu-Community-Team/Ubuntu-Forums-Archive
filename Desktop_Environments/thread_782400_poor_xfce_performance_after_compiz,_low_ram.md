---
title: "poor xfce performance after compiz, low ram"
date: 2008-05-04
forum: Desktop Environments
---

### Post by jecompton on 2008-05-04
I got 3d accel working, and then I monkeyed around w/ compiz. It was fun, but I like performance more than the cube. I switched back to plain xfce w/ xfwm4.

However, the performance seems poor for a recent laptop (amd64 w/ ~384MB ram). My debian desktop on a P4 256MB runs more smoothly.

Specifically, if I have firefox tbird, and a Terminal open, each on a separate workspace, switching between workspaces causes a slow redraw of the program on the new workspace. Starting even a simple program can take a minute or longer.

The xfce System Monitor applet shows memory at 90% or more used. cpu load is usually less than 20%.

Firefox takes the most ram at 164MB, spiking around 175MB during redraws. Everything else is below 10MB, and System Monitor only shows about 210MB being taken up total if I sum the items listed. Why is my ram so full?

---

### Post by jecompton on 2008-05-06
I switched over to Enlightenment (e16) for a while, but after a while, it became slow in switching between workspaces and programs as well.

this makes me suspect a memory leak, but I don't know how to track it down.

---

### Post by prshah on 2008-05-06
> **jecompton said:**
> I got 3d accel working, and then I monkeyed around w/ compiz. It was fun, but I like performance more than the cube. I switched back to plain xfce w/ xfwm4.

However, the performance seems poor for a recent laptop (amd64 w/ ~384MB ram). My debian desktop on a P4 256MB runs more smoothly.


Don't know about your RAM usage issue, but I had the same problems on xubuntu when I ran it's inbuilt compositing manager: You can disable it with Applications-Settings-Workspace tweaks (I think, not on xubuntu now, only ubuntu)

---

