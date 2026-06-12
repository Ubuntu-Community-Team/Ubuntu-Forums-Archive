---
title: "Nautilus Hangs whenever I access the root directory (/)"
date: 2007-02-18
forum: Desktop Environments
---

### Post by Vashu on 2007-02-18
Recently whenever i try to access / thru nautilus it hangs and consumes 100% of the processor. I have to kill it to make usable again.

Its odd because i dont remember installing anything that could have caused it and it also happens when i access a remote root directory thru ssh share.

I read a similar problem here: [http://ubuntuforums.org/showthread.php?t=346088&highlight=nautilus+locks](http://ubuntuforums.org/showthread.php?t=346088&highlight=nautilus+locks)

but it seems not to be my case since i dont think any thumnailing occurs on / and if it did i dont think i could fix it by just moving files around. And it seems to occur with network shares too.

Any idea what could be wrong?
Im using an up to date (at writing time) Ubuntu 6.10.

---

### Post by phoqueyoo on 2007-02-18
Similar thing happened to me (but in my media directory) and the problem ended up being a corrupt file. Have you tried simply doing a cd / && ls and seeing if that works or you could try using thunar. I fixed it by doing a fsck --rebuild-tree i beleive.

---

### Post by Vashu on 2007-02-18
I can access the root directory using the terminal, its seems to be only an issue with nautilus.

---

### Post by Vashu on 2007-02-19
anyone? Bump.

---

### Post by billstei on 2007-05-02
I am getting Nautilus severe slow downs whenever there is a large number of files in the dir I am browsing.  On Feisty AMD64 with dual core.

---

### Post by atonello on 2007-05-02
> **billstei said:**
> I am getting Nautilus severe slow downs whenever there is a large number of files in the dir I am browsing.  On Feisty AMD64 with dual core.
That's the same for me, too
(fresh install of 7.04 i386 - brand new /home)

I can see it happen also from firefox, anytime i right-click to save an image to a local folder: cpu at max speed and exasperating looong wait till it finally refreshes with the content of the destination folder.

---

### Post by billstei on 2007-05-02
Gnome bugzilla tracking this (I think) [http://bugzilla.gnome.org/show_bug.cgi?id=356836](http://bugzilla.gnome.org/show_bug.cgi?id=356836)

---

