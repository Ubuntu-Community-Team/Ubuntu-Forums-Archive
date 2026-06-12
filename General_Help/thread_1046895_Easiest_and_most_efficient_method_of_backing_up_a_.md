---
title: "Easiest and most efficient method of backing up a home Ubuntu pc"
date: 2009-01-21
forum: General Help
---

### Post by silverbullet007 on 2009-01-21
I'm in the market for a backup solution for my Ubuntu box.  After skimming through Synaptic and Googling I realize there are many different ways of accomplishing this... however I'm looking for a nice, easy to use gui.  Something that if I need to recover form a hdd gone south or an other major hardware failure I can install a blank Ubuntu setup, load the software then insert a DVD or even maybe plugin a USB hdd.

I've read thru the branch and website for [https://wiki.ubuntu.com/HomeUserBackup](https://wiki.ubuntu.com/HomeUserBackup) but it seems after three years it's not complete yet.

What do you guys use aside from a CLI app?  Does anyhitng exist like what I'm describing?

Thanks!

---

### Post by Slim Odds on 2009-01-21
Clonezilla

---

### Post by theWrkncacnter on 2009-01-21
grsync is a GUI frontend for rsync, which is one of the best. If you use it to make a backup of your drive on that USB hard drive, all you would have to in case of a problem is reverse the process and copy the data from your USB drive back to your harddrive.

You can also configure it to backup only what you want it to.

Edit: See this page for more ideas: [http://www.debianhelp.co.uk/rsyncweb.htm](http://www.debianhelp.co.uk/rsyncweb.htm)

---

