---
title: "Repository?Help"
date: 2006-04-18
forum: Desktop Environments
---

### Post by u0014 on 2006-04-18
I am trying to insatll "aboot-cross". This packgae appears in Synaptic Package Manager, ut when I try to install it tells me that package is not installable and that I should have the right repositories. Anybody can give me some suggestions or perhaps a repository that may add?

---

### Post by ape on 2006-04-19
This package (aboot-cross) is in the universe repository.  

Find the line in your /etc/apt/sources.list file that looks something like this:

       [FONT="Courier New"]deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) breezy main restricted
[/FONT]

and add 'universe' to the end of it so it now looks like:

    [FONT="Courier New"]deb [http://ubuntu.cs.utah.edu/ubuntu](http://ubuntu.cs.utah.edu/ubuntu) breezy main restricted universe[/FONT]


Now do a synaptic update and try installing the package again.

---

