---
title: "Add/Remove gui versus apt-get (searching)"
date: 2008-01-09
forum: Desktop Environments
---

### Post by tomhorsley on 2008-01-09
Never used ubuntu before, and I'm freshly confused. I installed 7.10 desktop, found there was no sshd, so brought up the Add/Remove programs gui to see if I could install it. I did indeed enable lots of software sources, and it reloaded the info, but when I say show me all available programs and type "ssh" or "openssh" or "openssh-server" in the search field, it says nothing matches my search.

I decide to try the command line tool instead, and type "sudo apt-get install openssh-server", and it spews a bunch of gibberish on my screen which seems to indicate it did indeed download and install sshd (and I can even ssh into the machine now).

Why the difference? It would be much more useful if I could search for the same stuff I can install with apt-get since I may not know the exact package name all the time.

---

### Post by luisromangz on 2008-01-09
Don't use Add/Remove, I think it is just for fresh ex-Windows users which might find good ol' Synaptic confusing (and they don't know about sshd).

---

### Post by mcduck on 2008-01-09
Add/Remove is made to be just a simple way of installing and uninstalling some of the most commonly used graphical applications. It's not supposed to be a full-featured package management tool, or to handle every piece of software available in repositories.

If you need a real graphical tool to manage your software, use Synaptic (in System/Administration/Synaptic Package Manager).

I actually use all three, Add/Remove, Synaptic and command-line tools. Add/Remove is nice when you are looking for a program without knowing exactly what you are looking for, for example when you wish to get some new game and you wish to browse through most popular games available. Command-line tools are great when you know exactly what you want (and the exact name of the package as well). For everything else, there's Synaptic. :)

---

### Post by tomhorsley on 2008-01-09
OK, I'll check out synaptic. Thanks.

---

