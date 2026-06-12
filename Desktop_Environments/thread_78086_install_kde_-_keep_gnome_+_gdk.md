---
title: "install kde - keep gnome + gdk"
date: 2005-10-17
forum: Desktop Environments
---

### Post by goneskiing on 2005-10-17
What is the best way to load the kde packages while maintaining gdk and gnome as default desktop

---

### Post by somuchfortheafter on 2005-10-17
sudo apt-get install kubuntu-desktop

---

### Post by goneskiing on 2005-10-17
This all seems broken:

1) I tried as mentioned - but I received a ton of "not found" msgs and it required me to put in my orignal CD which I thought was strange.  I guess it copied some of the packages from the CD but gave me an error that many of the packages were missing.

2) I couldn't find anywhere to adjust the repositories so I used synaptic - made sure I included all updates as well as universe.  Also I couldn't find anywhere, where I could select mirrors - I am in US so it is defaulting to US mirrors but my experience is that US mirrors usually suck big time and I'm much better off downloading from Europe.

3) With either Synaptic or Command line, I now get failure depending on broken package libgl1-xorg

---

