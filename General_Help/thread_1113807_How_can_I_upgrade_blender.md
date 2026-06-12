---
title: "How can I upgrade blender?"
date: 2009-04-02
forum: General Help
---

### Post by mahela007 on 2009-04-02
I installed blender about a month back. However instead of the latest version which i think is 2.8 I got version 2.6
I was satisfied with .6 until i realised that some tutorials were not compatible with 2.6
So how can i upgrade to 2.8?

---

### Post by Sam Lars on 2009-04-03
Did you install through Ubuntu (apt-get blender)?

---

### Post by wolfen69 on 2009-04-03
you could do
```
gksudo gedit /etc/apt/sources.list
```
and enable your backport repo.
then
```
sudo apt-get update
```
then install blender again.

after that, you might want to go back to your sources list and close the backports repo.

btw, the latest stable blender is version 2.48a

---

### Post by mb_webguy on 2009-04-03
Blender can be found in the [Ubuntu Bleeding Edge Team PPA]("https://launchpad.net/~ubuntu-bleedingedge/+archive/ppa").

EDIT:  I just realized that the Bleeding Edge team hasn't updated Blender since mid-2008, and is only v2.45.  You'd do better by downloading Blender from the [official website]("http://www.blender.org/download/get-blender/").

---

### Post by Meow27 on 2009-04-03
doesnt blender have its own linux binary for download?

---

### Post by mahela007 on 2009-04-04
Yes. I installed it via synaptic. and what is a backport repo? (I'm running kubuntu.)

---

