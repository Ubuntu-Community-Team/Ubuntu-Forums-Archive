---
title: "kubuntu 5.04 -&gt; ubuntu 5.10"
date: 2005-12-09
forum: General Help
---

### Post by outtacontrol on 2005-12-09
I have been using kubuntu but want to upgrade to ubuntu 5.10 (with gnome).  Is that possible w/o having to do a fresh installation?  I don't want to go through the hassle of moving all my files off the box and moving them all back on.

---

### Post by snowjunkie on 2005-12-09
I believe it would be.
Go through your /etc/apt/sources.lst, replacing "hoary" with "breezy".

Then do a 
```
sudo apt-get update
```
followed by
```
sudo apt-get dist-upgrade
```
This will upgrade you to Breezy 5.10.
Then you can install the ubuntu desktop using
```
sudo apt-get install ubuntu-desktop
```

Hope that helps.

sj*

---

### Post by outtacontrol on 2005-12-09
Have you ever tried it?

---

### Post by greeneagle on 2005-12-09
[QUOTE=snowjunkie]I believe it would be.
Go through your /etc/apt/sources.lst, replacing "hoary" with "breezy".

Then do a 
```
sudo apt-get update
```
followed by
```
sudo apt-get dist-upgrade
```
This will upgrade you to Breezy 5.10.
Then you can install the ubuntu desktop using
```
sudo apt-get ubuntu-desktop
```

Hope that helps.

sj*[/QUOTE]
I am assuming you can do this from ubuntu 5.04 to kubuntu 5.10 with the same logic?

---

### Post by dcast on 2005-12-09
I did it and my system got totally screwed so i just did a fresh install

---

### Post by greeneagle on 2005-12-09
Not exactly what I wanted to hear.

---

### Post by snowjunkie on 2005-12-10
[QUOTE=outtacontrol]Have you ever tried it?[/QUOTE]

I've done it the opposite way around:
Ubuntu 5.04 -> Ubuntu 5.10 -> Kubuntu 5.10

Didn't experience any problems.

sj*

---

