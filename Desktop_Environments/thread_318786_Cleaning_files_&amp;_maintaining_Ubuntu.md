---
title: "Cleaning files &amp; maintaining Ubuntu"
date: 2006-12-14
forum: Desktop Environments
---

### Post by tjk on 2006-12-14
I've been using Ubuntu now for a couple of months -- love it and won't run XP again.  However, I did install both VMWare player and server (as per the HOW TO files).  I had multiple crashes under VMWare and consequently reinstalations.  Finally I ran the uninstall in "synaptic package manager", but there are still remnants of it plus all of the VMWare server sitting in my partition.  How can I clean it off.

This brings up a second question about maintaining/cleaning files on Ubuntu.  I downloaded/installed a program called "KleanSweep" and it gave such outradgeous results (eg 3,000 orphaned files) that I uninstalled it.  I used aptitude and it ended up uninstalling KDE! (so I'm hesitant to try it again -- needs a newbie setting)  Now I use kdorphaned, but it seems very limited in what it does.  There must be large number of unused files that are doing nothing but taking up space on my harddrive, but there seems to be no package to deal with this problem.  The situation seems to be further complicated because I run multiple desktops and some programs don't work under all of them.  Please tell me that there is something out there that can cleanup/speedup my system (there a thousands out for Windows).

---

### Post by breezyfox on 2006-12-14
hi
well you can try
sudo apt-get clean
or
sudo apt-get autoclean
I don't know much how much it cleans.I think it works for apt i.e. unused packages only. Some one can put better light on that.

---

### Post by tjk on 2006-12-15
> **breezyfox said:**
> hi
well you can try
sudo apt-get clean
or
sudo apt-get autoclean
I don't know much how much it cleans.I think it works for apt i.e. unused packages only. Some one can put better light on that.

Isn't this a lot like aptitude -- afraid I might loose one of my desktops again.

Further to the cleaning of files...  I was browsing the files and found **four** files named "core" (actually one is kcore) that are nearly 1gig in size (all the same size and same date/time)!  Do I need all of these of them? What are they?

---

### Post by kalikiana on 2006-12-15
> **tjk said:**
> Isn't this a lot like aptitude -- afraid I might loose one of my desktops again.

No, these commands will only remove unused packages which are not used, for example if you had gtk installed but no gtk application it would remove gtk.

If you had problems with aptitude you might try synaptic as it can also remove unused packages but you can clearly check what they are before you delete them - this is what I do from time to time.

---

### Post by tjk on 2006-12-20
Thanks everyone for your tips.  

No one suggested using "KleanSweep" or mentioned that they had used it... I was wondering if anyone had any **good** experiences with this software?

---

