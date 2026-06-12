---
title: "[SOLVED] Upgrade to 8.10 Broke pulseaudio"
date: 2008-12-13
forum: General Help
---

### Post by AFarris01 on 2008-12-13
K... i had been holding off on upgrading to 8.10 because of school, and in case something went wrong, i didn't want to be without my computer.  well, finally yesterday i went ahead and upgraded, and everything appeared to go off without a hitch, except one thing.

My pulseaudio is now broken, and i don't know how to fix it. I first noticed it when i went to try and listen to some music in amarok, and i didn't have surround sound, and it said the first time i launched that xine couldn't initialize any audio drivers.  so, i tried cycling pulseaudio, but i then found out that it wasnt running at all.  now, every time i try to launch the pulseaudio daemon, i get this error message:

```
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.
```

what's all this about, and how do i fix it?  i appreciate any help that can be offered

---

### Post by kiisu on 2008-12-13
I was on Intrepid since September with no audio problems, until last week when pulseaudio broke for me too.
I didn't even do any updates!

I tried for several days to fix it but eventually I removed pulse. I know this isn't a proper fix but I've seen so many other audio problem posts recently I've decided just to keep my eyes on the forum until I see signs of a proper fix out there.

---

### Post by AFarris01 on 2008-12-18
you know what...i actually just fixed it.

it appears that the upgrade broke something in the default.pa file, causing the daemon to choke when starting up, since this is the default behavior of the daemon.

here's what i did to fix it:

open the daemon.conf file:

if you didnt create a personal daemon.conf then do:
```
sudo gedit /etc/pulse/daemon.conf
```
if you did, then you'll know where it is better than i...

anyway,
uncomment the line for 'fail' and change the value to no.
```
;fail = yes
```
change to:
```
fail = no
```

this is simply what i did to fix the issue... hopefully it will work for others as well!

---

