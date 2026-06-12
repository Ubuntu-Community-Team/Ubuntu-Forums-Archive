---
title: "XServer hangs on startup after installing more RAM and a new wireless card"
date: 2009-01-24
forum: General Help
---

### Post by eljaco on 2009-01-24
Hi,

I have a Dell PowerEdge 400SC server that I use as my desktop and am running ubuntu 8.10 on it. It was running fine and well until I just added some new RAM and a wireless card (used to be connected straight to router.)

The problem manifests when X starts - it just freezes after a few seconds and I can't use my keyboard or mouse. I entered in recovery mode and reconfigured my xserver, but when I ran "startx", it opens up my gnome session and the only thing I can see is a "User Switcher" error. I can go back to the terminal session (ctrl+alt+f1) and kill X and keep working that way, so it's not like the keyboard is completely frozen. When I run it normally (not recovery mode), I can't even type my username into the login screen.

Anyone have any clues or any commands I should run to see what is going on?

I also can't connect to any wireless networks, but it may be because I haven't configured it to connect to any SSID's. Just in case, it's a Realtek RTL-8185 b/g wireless card.

I dual-boot the machine with Windows XP and I can use that just fine with no issues (keyboard and mouse work, I can perform all my tasks without a problem.

Thanks in advance!

---

### Post by dcstar on 2009-01-25
> **eljaco said:**
> Hi,

I have a Dell PowerEdge 400SC server that I use as my desktop and am running ubuntu 8.10 on it. It was running fine and well until I just added some new RAM and a wireless card (used to be connected straight to router.)

The problem manifests when X starts - it just freezes after a few seconds and I can't use my keyboard or mouse. I entered in recovery mode and reconfigured my xserver, but when I ran "startx", it opens up my gnome session and the only thing I can see is a "User Switcher" error. I can go back to the terminal session (ctrl+alt+f1) and kill X and keep working that way, so it's not like the keyboard is completely frozen. When I run it normally (not recovery mode), I can't even type my username into the login screen.

Anyone have any clues or any commands I should run to see what is going on?
.......

Check the /var/log/Xorg0.0.log file and see if there are any obvious error messages, also the syslog file too.

It may be that new RAM is causing a problem - Linux pushes the hardware harder than Windows. Also see in the BIOS if the Wireless card is sharing an Interrupt with anything (like the video).

---

### Post by eljaco on 2009-01-25
I checked both log files, but neither show any errors. How can I check if the Wireless card is sharing an Interrupt with something else in the BIOS? I didn't see an option to do that when I entered the BIOS setup.

I am downloading a liveCD of 8.10 to make sure it runs fine with it - worst case scenario, I'll wipe out my ubuntu partition and install a fresh one.

---

### Post by eljaco on 2009-01-28
To add more info - I just tried running the LiveCD and it just hangs with a blinking underscore. I went into the alternative set-ups menu and had it use a driver CD (the wireless card's), and it hung on starting the Gnome Display Manager - maybe it is my Xorg after all? Shouldn't this work out of the box with a LiveCD anyways?

---

