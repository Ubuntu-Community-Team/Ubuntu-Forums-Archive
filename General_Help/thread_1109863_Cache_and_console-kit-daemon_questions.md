---
title: "Cache and console-kit-daemon questions"
date: 2009-03-29
forum: General Help
---

### Post by .Maleficus. on 2009-03-29
I've been monitoring htop recently and noticed that all of my free RAM is being cached.  I've got 220MB being used and the other 3730MB is cached.  Why is this?  Sometimes it'll even cause me to start using swap space which on a system with 4GB of memory I shouldn't have to do.

Also, are there any reasons why I would have ~40 instances of console-kit-daemon running?  Can I safely kill some of them?  This is on Arch if it matters.

Thanks guys.


Edit:  And if it matters, the only processes I've started so far are Firefox (5 tabs), ncmpcpp, htop and rtorrent.

---

### Post by sdennie on 2009-03-29
I don't know what console-kit-daemon is but, having huge amounts of RAM used as cache is both normal and desirable.  It makes your system much more response as it no longer has to read from disk for things you are commonly using.  However, if you have many instances of the same unknown application running and you are starting to use swap with 4G of memory, it probably means the processes is bugges and is just spawning off more instances of itself.  It's both being cached (good) but also generating so much pressure on memory on the system that you are using swap (bad).  It's very difficult to use more than 1G of RAM for "normal" desktop usage (and the rest of the 3G will eventually become cache (good)) so, essentially, there is something fundamentally broken within your Arch install.

---

### Post by .Maleficus. on 2009-03-29
Well, that's a bummer.  I guess it's not all bad though - I can try out ext4 without worry and finally make myself a /home partition.  Reinstall is a project for next weekend thought ;).

---

