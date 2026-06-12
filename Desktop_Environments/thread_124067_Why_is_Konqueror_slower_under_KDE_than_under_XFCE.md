---
title: "Why is Konqueror slower under KDE than under XFCE?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by holstein on 2006-01-31
I've tried out XFCE on my machine (P4 2.6, 512 mb ram) and to my surprise, when I started Konqueror, it started awfully faster than under KDE. Under KDE, clicking on my Konqueror icon would mean a wait of at least 6-7 seconds, sometimes as long as 10. 

But under XFCE, it's more around 2-3 secondes, 4 max.

Any idea what's wrong with my KDE settings? Is it kwin fault?

My machine is a P4 2.6, 512 mb ram.

Konqueror is started without any switches, just plain konqueror on the command-line.

---

### Post by aysiu on 2006-01-31
XFCE is just a lighter desktop environment than KDE, even though Konqueror is a native KDE application.

---

### Post by Adrian on 2006-01-31
[QUOTE=holstein]I've tried out XFCE on my machine (P4 2.6, 512 mb ram) and to my surprise, when I started Konqueror, it started awfully faster than under KDE. Under KDE, clicking on my Konqueror icon would mean a wait of at least 6-7 seconds, sometimes as long as 10. 

But under XFCE, it's more around 2-3 secondes, 4 max.

Any idea what's wrong with my KDE settings? Is it kwin fault?

My machine is a P4 2.6, 512 mb ram.

Konqueror is started without any switches, just plain konqueror on the command-line.[/QUOTE]

Something is wrong here. On my 700MHz Celeron laptop with 384MB RAM and a 4200RPM drive, it usually takes like 1 second for Konqueror to load in KDE. This is because KDE preloads one instance of Konqueror when it starts, so it's already active in the memory.

However, even this is disabled, it never takes more than 5 seconds, and this is on my *slow* system.

---

### Post by holstein on 2006-02-01
Ok, I've created a new account for testing: Konqueror is showing the same kind of speed that I have under XFCE. (which is still at least around 2 seconds...)

So, this means that something is going wrong in my KDE configs. But what? I would guess this is not specific to Konqueror, since it is starting fast and fine under something else... So, some settings for kwin? Or global to KDE?

Sad, but it seems that I will have to trash (well, move...) my .kde and take things back in until I get the problem. Hum, sounds time-consuming... :( 

Or I can stay in XFCE. A few things missing here and there, but I guess that with some digging and tweaking... But then, I will have to switch to another forum. ;P

Thanks for your input

---

