---
title: "[SOLVED] Gnome desktop and VNC wierdness"
date: 2008-08-25
forum: Desktop Environments
---

### Post by csogilvie on 2008-08-25
I'm new to Linux, so please bear with me!

I recently built up a new machine running 8.04 64-bit.  (Was running 32 bit last week...  changed it to 64 today)

This machine was purchased to help me with work so I don't clobber the newly purchased 1u 8.04LTS server from the nice folks at system76.

I successfully setup SSH server, and tightvnc to let me SSH to my home computer from anywhere.

However, when I did, the layout of Gnome Desktop in both in the vnc session:1) and on the console session:0 started changing.

Spacing between the elements on the app panel at the bottom of my screen as well as the "power" button in the top right...  It's now a green stick-man who looks like the "exit" guy on every exit sign I've seen in Japan.

Any ideas how to reset it back to the default power button?

I've tried the desktop themes to no avail.

Any help is appreciated!

---

### Post by csogilvie on 2008-08-25
It looks like the problem was "user failure" which of course is the reason for 99% of IT help calls!

I was running 2 instances of Gnome with the same user.  (Me)

So it was getting very confused which made the display elements go wonky.


I love solving the problem myself!  lol

---

