---
title: "Compiling Wesnoth and other stuff..."
date: 2007-03-18
forum: Gaming &amp; Leisure
---

### Post by Crushyerbones on 2007-03-18
I've been trying to compile Wesnoth 1.3.1 from it's source but I can't because I need a "python development package" What's this, where can I get it, and why doesn't it come with the python packages already?

I've been searhing google the whole day and found no results so far... And it's not just Wesnoth but It's what I'd like to use the most :mad: :lolflag: 

Please help a Ubuntu noob out

---

### Post by Denta on 2007-03-18
Look in the repos for **python-dev**.

---

### Post by Perfect Storm on 2007-03-18
It's python2.4-dev for compiling wesnoth.

---

### Post by Crushyerbones on 2007-03-18
Any idea where I can get those tough? .deb or easier if possible, as I'm having problems compiling Python too :p

---

### Post by Perfect Storm on 2007-03-18
You don't need to compile stuff in Ubuntu, you might want to search or make some research on synaptic package manager and how to set it up (like extra repo etc.), You can find it in System --> Adminstration ----> Synaptic.

To do it through commandline;
```
sudo aptitude install python2.4-dev 
```

---

### Post by Crushyerbones on 2007-03-18
> **Artificial Intelligence said:**
> You don't need to compile stuff in Ubuntu, you might want to search or make some research on synaptic package manager and how to set it up (like extra repo etc.), You can find it in System --> Adminstration ----> Synaptic.

To do it through commandline;
```
sudo aptitude install python2.4-dev 
```


I already did that on synaptic... I tought the dev package was something different... I've got all the python packages on synaptic installed but it still says I need the python development package.

Edit: It seem I've got more python packages than before for some reason... I'll try recompiling Wesnoth again in a while to check if it works now

---

### Post by Perfect Storm on 2007-03-18
Please attach you whole ./configure in a text file to a post, it's easier then.

---

### Post by Crushyerbones on 2007-03-18
It all works now... (Atleast I can use the make command now), must have been a corrupted download, packages in use or something similar... Thanks for all the help. Anyone want a wesnoth 1.3.1 binary when I'm done?

---

