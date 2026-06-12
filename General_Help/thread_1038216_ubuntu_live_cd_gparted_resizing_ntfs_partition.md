---
title: "ubuntu live cd gparted resizing ntfs partition"
date: 2009-01-12
forum: General Help
---

### Post by bedake on 2009-01-12
Hello, I am in the midst of resizing my windows ntfs partition using gparted on the ubuntu live cd.  It has been working on the step:

ntfsresize -p --force --force /dev/sda1 -s 98423668223

its been on this command step for like 10 minutes now.

I am assuming this isnt normal, the working light on my computer is going as if it is still processing something but it doesnt seem to be progressing.

Any advice on what I should do would be apprectiated, If i cancel the resize will my windows partition be ruined?



I tried using gparted but my monitor had no display on it, maybe a newer version would work

---

### Post by taurus on 2009-01-12
I would not cancel it.  And by the way, it's probably best if you defrag your harddrive (windows partition) a few times before you try to resize it.

---

### Post by bedake on 2009-01-12
Well I feel like an idiot, it just finished sorry for my impatience

---

