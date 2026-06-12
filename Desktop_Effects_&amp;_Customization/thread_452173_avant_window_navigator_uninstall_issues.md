---
title: "avant window navigator uninstall issues"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by mjmcdonald21 on 2007-05-23
I tried out AWN but must have screwed up somewhere when I tried to uninstall it.  The program still loads from the Applications menu but I am unable to remove it with the following.

```
sudo apt-get remove avant-window-navigator avant-window-navigator-svn affinity-tracker affinity-beagle affinity-svn

```

Even if I am unable to remove the application I would still like to remove it from the menu.  Any help would be great.  Thanks.

---

### Post by kpolice on 2007-05-23
You don't have it installed that's why it doesn't uninstall anything.

Try only sudo apt-get remove avant-window-navigator-svn or even easier use synaptic.

---

### Post by mjmcdonald21 on 2007-05-23
Unfortunately it wasn't that simple or I did something wrong.  Here is what I got..

---

### Post by mjmcdonald21 on 2007-05-23
Sorry to bump my thread again but I'm completely lost on what to do here.

---

### Post by kpolice on 2007-05-23
That's really weird, you don't need all those packages to run awn so something is definitely wrong.

---

### Post by strumluff on 2007-05-23
How did you install awn in the first place? 

Did you compile from source, use a 3rd party repo or a pre-made deb?

---

### Post by mjmcdonald21 on 2007-05-23
I followed a tutorial somewhere and had to use the "make install" command I believe.  Sorry that I can't provide many details.

---

### Post by strumluff on 2007-05-24
Ah yes, so what you did was compile from source. You won't be able to uninstall using apt-get or synaptic because it wouldn't have made a package like that.

In order to uninstall you need to go to the folder that contains the source code (the directory with the makefile) for awn. Navigate to this folder in the terminal (using cd) and then type 

```
sudo make uninstall
```

This will uninstall it.

---

### Post by mjmcdonald21 on 2007-05-25
Problem solved.  Thanks!

---

