---
title: "Desktop search for KDE 4"
date: 2010-05-31
forum: Desktop Environments
---

### Post by lightningfox on 2010-05-31
Hello

I'm using Ubuntu 9.10 with KDE 4.

I want a desktop search program for KDE 4 like GNOME has beagle and tracker.

I know about Nepomuk but it seems too slow and resource heavy.

When I used to use KDE 3 I used a desktop search program called Kerry (a KDE frontend to Beagle) but I don't think has a KDE 4 version.


Please suggest a good desktop search program for KDE 4.

---

### Post by inobe on 2010-05-31
please explain exactly what you mean when you say resource heavy, i am not following ?

the amount of memory by default is merely 50mb's, surely you have sufficient memory, if not configure it by moving slider bar towards left to reduce memory usage.

---

### Post by TuxLove on 2010-06-01
I'm with lightningfox on this. System Activity shows strigidaemon typically consuming 10-12% of CPU - and I'm only indexing four not very large folders!

This seems borne out by this KDE bug: 

[I]"On many systems file indexing slows performance to an unacceptable level, and
indexing seems to be updated very frequently.  It would help if it were
possible to enable indexing at certain times of day, overnight, or times when
workload is lighter."[/I]
[https://bugs.kde.org/show_bug.cgi?id=226773](https://bugs.kde.org/show_bug.cgi?id=226773)

---

### Post by sidzen on 2010-06-01
Have either of you considered and/or tried the** L**ight** X**11 **D**esktop **E**nvironment (LXDE) that is  ***lubuntu***'s desktop?
One can still incorporate selected KDE programs, if desired.

---

### Post by lightningfox on 2010-06-06
By resource heavy I mean it uses up a lot of RAM.

I haven't used LXDE but I'll try it.**

---

### Post by Barafu Albino Cheetah on 2010-06-07
Beagle itself is not depending on windows manager. It has a GTK, not gnome-dependent default front-end. It is perfectly usable with KDE, XFCE, FluxBox, MyCoolDIYWM or anything. 
Kerry was just providing KDE kio slaves based on beagle queries. It is not being developed for some time already? but you don't loose much.
Nepomuk eagerly tries to index my files, eats up space, but always returns weird results. It is not usable yet.

---

### Post by Kilroy2011 on 2011-02-22
**Is there a way to include beagle/kerry into kubuntu 10.10?**

It is not listed in the installable software anymore. I'm not too familiar with the overall installation procedure, but I tried to get beagle for my system. No success.

I tried to use a version I found in a repository, but installation failed due to many dependencies, that were too new now. :(

Kilroy

---

