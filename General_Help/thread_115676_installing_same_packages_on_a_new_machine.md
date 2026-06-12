---
title: "installing same packages on a new machine"
date: 2006-01-11
forum: General Help
---

### Post by danyul on 2006-01-11
Hi all, 
I'm running Ubuntu Breezy on both my desktop and my laptop.  After weeks of exploring/apt-getting/synaptic-ing/fooling around, I have a large amount of packages installed on my desktop that I would now like to install on my laptop.  What's the easiest way to apt-get on my laptop the same packages I installed on my desktop?  I know I could just read from my history log in synaptic, manually apt-getting whatever I see on my laptop.  But as there's hundreds of packages, I was wondering if anybody knows of an easier, more automated way?
Best,
Dan

---

### Post by felix_stegerman on 2006-01-11
Hi,

You can use
# dpkg --get-selections
and
# dpkg --set-selections

See man dpkg for more information.


Felix

---

### Post by lamego on 2006-01-11
Copying /var/cache/apt from the installed system will also save you some time and bandwith.

---

### Post by danyul on 2006-01-11
thanks for the tips...

---

