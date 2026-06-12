---
title: "Metacity memory leak?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by Vidar on 2005-10-31
I can't find another explanation for this problem anyways...

On my stationary workstation, it's not uncommon that **metacity** itself uses about 90mb of Resident Memory and well over 200mb of Virtual memory. **Nautilus** comes in as a close second though, with about 50 mb of Resident Memory and over 200mb of Virtual Memory consumed... this system only carries about 512mb of ddr2-ram, so it's a bit on the heavy side... 

However, if I kill the process for metacity and let it restart itself, it will only use about 8mb of Resident and 12mb of Virtual Memory, so I figure that somehow it allocates more memory for itself over time. Last time I checked, the workstation had an uptime of 11 days and metacity consumed about 300mb of system memory, together with nautilus making the system next to unusable (still stable as a rock thought, thank god for that).

Any ideas about what to do to help eliminate this problem, apart from filing a bug in bugzilla? Is this a known bug or am I just unfortunate? Perhaps it's a feature of metacity that's using all that ram, and Im just being ignorant?

Please enlighten me. :)

---

### Post by Vidar on 2005-10-31
The same thing with **nautilus**, after I've killed the process and it's restarted, it's back to a sound 13mb of memory use...

---

### Post by Vidar on 2005-11-04
Hmm, same problem still... after a few days my memory gets clogged with nautilus and metacity...

---

### Post by u-blunt-2 on 2005-12-15
My metacity stalls when i log into Ubuntu. It started after some problems using Open Office Impress. Now everytime I logon, I have to wait a good minute or two for it to work... 
Theres something sketchy with it for sure

---

### Post by hollowhead on 2005-12-16
Maybe this explains why nautilus crashes I find it very unstable.  Then it restarts whether I want it to or not......

---

### Post by fct on 2005-12-16
Nautilus uses caches to improve disk access, so it's normal that it accumulates some memory after some time being used.

About metacity, no idea, but I always have an applet monitoring memory use and I see nothing wrong there.

You could contact the people at this mailing list if you really think there is a memory leak there. They might tell you which tools you can use to help them locate the problem:

[http://mail.gnome.org/archives/performance-list/](http://mail.gnome.org/archives/performance-list/)

---

