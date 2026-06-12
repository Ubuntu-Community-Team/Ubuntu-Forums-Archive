---
title: "DESPERATE HELP..upgraded 5.04 to 5.10. Gnome is ruined"
date: 2006-01-07
forum: Desktop Environments
---

### Post by corstar on 2006-01-07
I have really screwed up my system. I upgraded from within 5.04 to 510 and now, I can only log into xterm. Nothing gnome related works. The repositores are still stuck on hoary and I have one that refers to breezy and that's the dvd drive...PLEASE HELP ME. I really don't want to format, I'll got too much stuff on the drive.

---

### Post by corstar on 2006-01-07
geez, don't all rush at once to help me :(

---

### Post by Randomskk on 2006-01-07
If you have the HDD space, you could probably install KDE and use that to resolve the problem.
From an xterm, you can edit the source list (sudo vi /etc/apt/sources.list), change hoary to breezy (":%/hoary/breezy/g" in vi will do this for you, although doing it manually might be safer) and then save, sudo apt-get update, sudo apt-get install kubuntu-desktop. Once it's done, (and make sure you set the manager to use KDM instead of GDM, you get the option while apt is doing it's thing) restart and you should be able to select KDE as your session type.

From there, hopefully, you'll have a working interface to try and fix the problem.

---

### Post by corstar on 2006-01-07
Hey thanks for the reply. HDD space is not an issue.
Well, I managed to get some older repos working and slowly built up a few gui's
blackbox and xfce are nice enough for now.
I was just at a point today where I finaly compiled a bunch of apps that have never worked for me. I had everything perfect, then I broke it. Oh, well gnome at least.
I guess it was time for a change anyway.
Thanks guys

---

### Post by pauljwells on 2006-01-07
I can't see why Gnome shouldn't be fixable - if you have an xterm you can nano your /etc/apt/sources.list and then apt-get update then apt-get dist-upgrade.

How did you upgrade to 5.10 anyway?? The **right** way is to change all the 'hoary's to 'breezy's in the sources list and run apt-get anyway. You coud still try this and see if the magic of apt will fix your system, it could well be a screwed up dependecy

---

### Post by corstar on 2006-01-07
the way I done it was inserting the cd whist hoary was running, then, it updated a bunch of things in synaptic and applied, little did I realize it had removed nautalis, ubuntu-desktop and every other essential thing.
But, I'm over it now. I'm really enjoying Xfce.
Thanks for your help though.

---

### Post by corstar on 2006-01-07
All is good now.
I managed to update the repos and get the parts that were missing off the cd.

Well, I'll put this on down to experience and I've leared a little bit more about linux.

---

### Post by pauljwells on 2006-01-07
The best way to learn about linux is to break it and then try to fix it again ;) 

It's essential to have another computer though, so you can access the forums while you figure it all out!

Experience is always gained immediately *after* it would have been most useful...

Oh, and remember you have to reboot after a kernel change, of course

---

### Post by corstar on 2006-01-07
YEAh. I've broken it heaps of times.
I had my laptop here, but I wanted to see if I could figure it out for myself. 
Everything is cool now
:cool:

---

