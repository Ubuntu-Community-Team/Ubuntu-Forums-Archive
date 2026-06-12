---
title: "Timed Shutdown"
date: 2008-12-10
forum: General Help
---

### Post by Jontyy on 2008-12-10
i have read in some other posts that you can do a timed shutdown with:
sudo shutdown 20:00 or something like that, does this force quit all applications?

by the way, could somebody recommend me some anti-virus/spyware applications

thanks

---

### Post by Titan8990 on 2008-12-10
Close, it would actually be this:

sudo shutdown 20:00 -h


> by the way, could somebody recommend me some anti-virus/spyware applications

You don't need one unless you plan to use it scan your windows drive. If that is the case:


sudo apt-get install clamav

---

### Post by ajcham on 2008-12-10
> [QUOTE]by the way, could somebody recommend me some anti-virus/spyware applications

You don't need one unless you plan to use it scan your windows drive.[/QUOTE]

An AV scanner is also useful if you intend to share files with Windows users, as an act of courtesy if nothing else.

---

### Post by Jontyy on 2008-12-10
would sudo shutdown 20:00 -h force quit all applications?
vuze doesnt allow me to shutdown after stuffs downloaded and i dont want to keep my pc on all day when im at college.

i plan on using AVG or something like that on the windows partition, do i not need any software like that for intrepid?

cheers

---

### Post by Titan8990 on 2008-12-10
> would sudo shutdown 20:00 -h force quit all applications?

It will only "force" quit them if they refuse to shutdown cleanly: [http://en.wikipedia.org/wiki/SIGTERM](http://en.wikipedia.org/wiki/SIGTERM)

Under the "usage" section of that wiki article it explains how shut down will kill your running apps.


> i plan on using AVG or something like that on the windows partition, do i not need any software like that for intrepid?


No, linux does not need an anti-virus. If you search the Security Discussion forums, there is a post on it about every other week.

---

### Post by northern lights on 2008-12-10
> **Jontyy said:**
> i plan on using AVG or something like that on the windows partition, do i not need any software like that for intrepid?
If you keep AVG running in the background under Windows, you'd only need an antivirus app under Ubuntu if you meant to share files from it with other Windows machines (and cared for their survival) - see ajcham's post.

---

### Post by Keith Hedger on 2008-12-10
> **Jontyy said:**
> would sudo shutdown 20:00 -h force quit all applications?

yes the shutdown is forced you can also use relative times instead of an actual time or "now" to do it straight away you can also use -r to do a reboot instead of a halt, see the man pages

---

### Post by Jontyy on 2008-12-10
all right, sorted, cheers for everyones help

---

### Post by Mazin on 2008-12-10
An alternative for timed events is saying something like ```
sleep 20m && shutdown
``` or ```
sleep 1h && ./batch.sh
```, except you will have to already be root if you want to do the task as root.

---

