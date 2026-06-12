---
title: "Creating empty 750MB ISO file"
date: 2007-03-18
forum: Desktop Environments
---

### Post by elreteipos on 2007-03-18
I would like to make an empty ISO file with the size of 750MB. Afterwards, I want to mount it and "burn" some data on this virtual CD. Is that possible?

---

### Post by yabbadabbadont on 2007-03-18
"man mkisofs" has the answers (and more) to your question.  :D

---

### Post by elreteipos on 2007-03-18
I read the manpage, but I'm still too new to Linux to figure out what parameters I need. Can you please give me an example that creates an empty 700MB CD image? :)

---

### Post by yabbadabbadont on 2007-03-18
You don't create an empty image, there isn't any point.  Just create a directory tree on your harddrive that contains everything you would like to be in the image.  Then run mkisofs on that directory to create the actual image file to be burned.  :)

---

### Post by hardyn on 2007-03-18
the purpose of an emty ISO is to cheat the minimum shared data restrictions on p2p file sharing servers... am i correct? ;)

---

### Post by elreteipos on 2007-03-18
> **yabbadabbadont said:**
> You don't create an empty image, there isn't any point.  Just create a directory tree on your harddrive that contains everything you would like to be in the image.  Then run mkisofs on that directory to create the actual image file to be burned.  :)That won't work in my situation. I want to burn a VCD with a CD burning program, but I want to try it on a virtual CD before doing it for real. That's why I need to mount an empty ISO image.

---

### Post by yabbadabbadont on 2007-03-18
> **elreteipos said:**
> That won't work in my situation. I want to burn a VCD with a CD burning program, but I want to try it on a virtual CD before doing it for real. That's why I need to mount an empty ISO image.

Good luck.  :)

---

### Post by elreteipos on 2007-03-18
You mean it's probably not possible?

---

