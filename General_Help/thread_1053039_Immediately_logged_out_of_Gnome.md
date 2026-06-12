---
title: "Immediately logged out of Gnome"
date: 2009-01-28
forum: General Help
---

### Post by snikeris on 2009-01-28
Hi all,

This morning I received a series of updates, several of which involved the kernel.  These updates may or may not have been the source of the problem; I hadn't restarted the machine in over a week.  

I restarted, as instructed by the package manager, to find out that upon entering my username and password, I was immediately logged back out.  Gnome noticed this, and presented a dialog that displayed [~/.xsession-errors]("http://joe.snikeris.com/.xsession-errors").

I have an Asus video card with the nVidia 9600GT chipset, and I'm running 8.10.  I tried reinstalling all packages with the name 'nvidia' in them to no avail.  I'm currently using this [xorg.conf]("http://joe.snikeris.com/xorg.conf") in an effort to simplify things.

Here is my [Xorg.0.log]("http://joe.snikeris.com/Xorg.0.log")

Does anyone have any suggestions on how I should proceed?

---

### Post by snikeris on 2009-01-28
Update:

I've created a new user, and it has no problems at all logging in.

Therefore, the problem must be with something that is being run or some configuration changes I made with my normal user.  Where should I start looking?

---

### Post by snikeris on 2009-01-28
Solved:

I had an empty ~/.xsession

---

