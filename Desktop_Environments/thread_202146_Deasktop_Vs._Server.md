---
title: "Deasktop Vs. Server?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Breezy Badger on 2006-06-22
You think I would get my shit together, but perhaps this is so simple I just can't understand.

Someone tell me what the diff is between the desktop version and the sever version.  I was under the impression that desktop was just a version to install and see if you liked it first, but server was the real deal just pop in the cd and straight install it.

something tells me I am wrong.  I installed server and I got no desktop.

I had to do sudo apt-get install ubuntu-desktop

as we speak its installing the desktop on my other computer.

What am I missing here, should I not have installed server?

---

### Post by nanotube on 2006-06-22
[QUOTE=Breezy Badger]You think I would get my shit together, but perhaps this is so simple I just can't understand.

Someone tell me what the diff is between the desktop version and the sever version.  I was under the impression that desktop was just a version to install and see if you liked it first, but server was the real deal just pop in the cd and straight install it.

something tells me I am wrong.  I installed server and I got no desktop.

I had to do sudo apt-get install ubuntu-desktop

as we speak its installing the desktop on my other computer.

What am I missing here, should I not have installed server?[/QUOTE]

the server version is the linux without gui, for servers (naturally). the desktop version is basically the server version, with the graphical stuff on top of it.

so installing server, and then installing ubuntu-desktop, is the same thing as installing the desktop version.

hope that clears it up :)

---

### Post by Breezy Badger on 2006-06-22
Hey thanks man.

So does that mean now that I did sudo apt-get install ubuntu-desktop I have the desktop version and there is no need to reinstall with desktop?

thanks

---

### Post by nanotube on 2006-06-22
[QUOTE=Breezy Badger]Hey thanks man.

So does that mean now that I did sudo apt-get install ubuntu-desktop I have the desktop version and there is no need to reinstall with desktop?

thanks[/QUOTE]
yes, that's exactly what it means :)

---

### Post by Breezy Badger on 2006-06-23
awesome.  hey I got a good question maybe you know, if not ill start a new thread.

my mouse does not work, and I assume all my usb stuff (but have not checked yet).  the cursor is frozen, but if I unplug it and plug it back in..poof it works fine... I have to do this everytime to make it work

any ideas?

---

### Post by nanotube on 2006-06-23
[QUOTE=Breezy Badger]awesome.  hey I got a good question maybe you know, if not ill start a new thread.

my mouse does not work, and I assume all my usb stuff (but have not checked yet).  the cursor is frozen, but if I unplug it and plug it back in..poof it works fine... I have to do this everytime to make it work

any ideas?[/QUOTE]
hmm, no, i don't know the solution to this one. so start a new thread. :)

---

### Post by Breezy Badger on 2006-06-23
ok thanks again

---

### Post by Breezy Badger on 2006-06-27
***Follow Up****

I realized they are not quite the same after installing the desktop version.  The server version, even if you dl desktop on it, does not get the same updates....and likely other small things

go desktop if you want desktop

---

### Post by az on 2006-06-27
[QUOTE=Breezy Badger]even if you dl desktop on it, does not get the same updates....[/QUOTE]
Really?  That would mean that you are not using the same sources.list, but I am unaware of a different repo for the server packages....


Also, the kernel is different, which would probably explain why your mouse is not working.  Install linux-386 to get the desktop kernel.  The server kernel does not have a lot of desktoppy things...  It doesn't even boot on some pentium ones.  What is interesting is that the server installer kernel (on the cd) is the 386 desktop kernel, different from the one that gets installed (on your hard drive).

---

### Post by Breezy Badger on 2006-06-27
Well it would appear the mouse is not specific to the server ed.  Exact same problem with teh 386 desktop kernel.  Another person on the forum has the exact same problem.  Its the specific mouse, MX900 that is causing the problem.

---

