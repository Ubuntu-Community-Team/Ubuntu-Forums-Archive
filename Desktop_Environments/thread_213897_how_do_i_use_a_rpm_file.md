---
title: "how do i use a rpm file"
date: 2006-07-11
forum: Desktop Environments
---

### Post by sebweb on 2006-07-11
i am a noob who cant figure out how to use a program i recently got 
but it is an rpm file how do i use this
ps: did i mention i am a noob

---

### Post by T700 on 2006-07-11
Please see the link in my sig for directions on installing anything in Ubuntu.

Paul

---

### Post by xodus1 on 2006-07-11
install alien :
sudo apt-get install alien

then run:
alien -i /package

package is the name of the rpm aswell as the directory it is in /home/user/package.rpm

---

### Post by mcduck on 2006-07-12
if possible, you should install things from Ubuntu repositories, or use .deb packages. If those aren't available converting .rpm's to .deb with alien sometimes works, but rpm isn't native format for Ubuntu and might not work smoothly (or at all)

What program are you installing? Have you checked if it's available in Synaptic?

---

