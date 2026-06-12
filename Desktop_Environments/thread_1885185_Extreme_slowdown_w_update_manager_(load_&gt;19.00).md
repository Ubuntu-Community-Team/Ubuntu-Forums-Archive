---
title: "Extreme slowdown w/ update manager (load &gt;19.00) w/out &lt;0.50"
date: 2011-11-22
forum: Desktop Environments
---

### Post by krack3rz on 2011-11-22
So I have a big problem, everytime I start the update manager and press on install updates, or it pops up by itself telling me there are updates, system goes off into a grinding halt

I managed to get some screenshots, obviously the uptime dropped a bit before the print command (from keyboard) even responded, but it still illustrates what I mean:

1.
[http://img560.imageshack.us/img560/9187/screenshotat20111122154.png]("http://img560.imageshack.us/img560/9187/screenshotat20111122154.png") - image of whole screen with update manager

2.
[IMG]http://img403.imageshack.us/img403/9187/screenshotat20111122154.png[/IMG]

I was lucky this was open wen I took the screenshots.
Like I said in the title, the highest point in load averages was just shy of 20.00, with my specs thats impossible, especially since without the update manager everything works fine, less than 1.0 load average all the time.

_Info and specs:_
Ubuntu 11.10 - Unity with cairo-dock (autohide, thats y u cant c it)
```
uname -a
```
Linux krack-comp 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

The update manager has 80 updates I didnt install yet (because of severe slowdown, I'll hold it off for now)

Asus P5k Premium Black pearl ED, Mushkin 2GB RAM, dual core 2.66GHz Intel, Geforce GTX285 (Zotac).

_Biggest Running apps:_
~30 tabs Chrome, xchat, qbitt, 4 jedit files open in one window, 2 terminals (doing nothing)

After I closed update manager (which was grayed out), system went back to normal pretty fast (~5 min ->   <1.00 load)



Any other info that could help let me know.

Also, since I want to learn more about linux, I use chances wen system fails in some way to learn and fix it, please try to help without going for "reinstall" right away, i know thats the easy way out, which is my last resort (too many apps and stuff)

---

### Post by jerrrys on 2011-11-24
could you open a terminal and enter:

sudo apt-get update

and post any errors

---

### Post by krack3rz on 2011-11-25
> **jerrrys said:**
> could you open a terminal and enter:

sudo apt-get update

and post any errors

No errors, business as usual.
Just urls and:
"Fetched 72 B in 2s (31 B/s)
Reading package lists... Done"

Computer doesnt seem to slow down wen using the terminal so I figure its the update-manager prog itself or wat it interacts with; on a similar note, software-center does the same thing...its super slow, even if its installing one package.

---

### Post by jerrrys on 2011-11-25
I have also found update-manager a bit buggy and one reason I do not have it installed.

Instead  i use synaptic package manager for downloads and updates.

You may want to use it until you can find a fix for update-manager.

sudo apt-get install synaptic

---

### Post by krack3rz on 2011-11-25
yea I have it and you're right, it is normal, and doesnt slow down the pc like the those 2...

Too bad I cant find out why they are so slow...

---

