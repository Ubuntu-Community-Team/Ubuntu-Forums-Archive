---
title: "X question"
date: 2011-02-15
forum: Desktop Environments
---

### Post by QuantumFireball on 2011-02-15
I have a really old Dell computer (Dell PowerEdge 1300) that I am wanting to use as a small server (samba file server and apt-cacher-ng). I installed Ubuntu server and then did "sudo apt-get install --no-install-recommends ubuntu-desktop" which was a bad idea because it killed the performance.

So here is my question.
Ive read you can split the X client and server. Would that let me run a graphical program (like Synaptic) over X without installing any sort of GUI on the Dell?

If that is the case, how would I go about doing so?

If I would still have to install a GUI on the Dell, what are other options since the on-board display adapter seems to struggle with graphics?

---

### Post by mikewhatever on 2011-02-15
The other options depend on what you want from the GUI, but generally, running xserver itself is probably the biggest strain.

---

### Post by mr_luksom on 2011-02-15
Only 64MB RAM? Definitely not gnome ubuntu. Maybe, and I mean maybe, you could install lubuntu that uses lxdm rather than gnome:

```

sudo apt-get install lubuntu-desktop

```

Psychocats has a good guide for getting rid of the gnome stuff if you want to Google it. Otherwise, I'd be looking at a new distro like puppy or dsl.

---

### Post by QuantumFireball on 2011-02-16
64 mb? I have 256 MB in it. I actually stumbled upon webmin which seems to be working quite nicely for the moment.

---

