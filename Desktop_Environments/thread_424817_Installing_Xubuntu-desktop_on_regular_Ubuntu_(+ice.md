---
title: "Installing Xubuntu-desktop on regular Ubuntu (+icewm)"
date: 2007-04-27
forum: Desktop Environments
---

### Post by Skerit on 2007-04-27
I've recently made a "mediacomputer" out of one véry old piece of hardware (Pentium II (300MHz or so), 64mb ram) Since regular gnome is kinda sluggish (kinda a lot) I decided to install icewm, ofcourse that's ugly as hell so I thought, why not try xubuntu? Because reinstalling on this overdriven typewriter would take ages, I just installed xubuntu-desktop but now I don't see "XFCE" or "Xubuntu" in the session-chooser, only IceWM and Gnome and Xterm and all ...

Any hints?

---

### Post by Pugwash on 2007-04-27
Thats wierd. Did you do "sudo aptitude install xubuntu-desktop" ?

---

### Post by Skerit on 2007-04-27
Yes, well, with apt-get, but that's the same. 

I have to point out the installation got interrupted, insufficient disk space, but I removed some other programs and it continued flawlessly.

---

### Post by DJiNN on 2007-04-27
Just a thought, but on a machine that old (But still highly useable i might add) i would be inclined to do a "Server" install with just a base system (ie: no Window Manager or X etc) then add everything that i needed from there. It will take up less space & "Should" be a lot faster. Using IceWM is a good choice, but there's always OpenBox & FluxBox as well. Both are very lightweight & would do the job admirably. 

I think you'll find that XFCE may be a little sluggish (When compared to the likes of Ice/Flux/Open etc) on that machine, especially when it's installed with all the other stuff that comes with the Xubuntu desktop.

DJiNN

---

### Post by Skerit on 2007-04-27
Yeah, I realized this when it was too late, at first installing a command-line only kinda looked scary to me, I've been using Linux for nearly 2 years now but still, I thought I really would have to do everything myself, I didn't know it would sitll be as easy as ever. And the install took hours and hours, so I didn't look back. I should have.

I'm gonna search some more info on fluxbox, for some reason xfce and fluxbox are the same in my mind, I just thought about trying xubuntu because I thought it might make things easyer, more ubuntu-ish.. 

Anyway, it's on my todo list for next week :)

---

### Post by x1a4 on 2007-04-27
Hi, 

Since your installation was interrupted, you might not be getting Xfce because it isn't configured.  Try: 

dpkg --configure -a

to configure all unconfigured packages.

---

