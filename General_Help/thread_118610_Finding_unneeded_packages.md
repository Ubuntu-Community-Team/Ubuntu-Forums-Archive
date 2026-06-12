---
title: "Finding unneeded packages"
date: 2006-01-17
forum: General Help
---

### Post by bagel on 2006-01-17
Hello there;

I just asked myself if there is an easy way to list all the packages that have no dependencies. I'm thinking about cleaning up my system a bit, and there might by some libraries lurking around, without programs needing them anymore.

(With "easy" I mean fast (-: The shell does not scare me)
Excuse me if there is a trivial option to dpkg i overlooked, thanks in advance,

Bagel

---

### Post by earobinson on 2006-01-17
you could start by uninstalling programs you dont use.

---

### Post by newuser111 on 2006-01-17
sudo apt-get install deborphan

deborphan lists packages that have no dependencies and can be safely removed

---

### Post by earobinson on 2006-01-17
wow, never new that :), you really do learn something every day.

Thanks newuser111. I will be installing this for sure.

---

### Post by niviche on 2006-01-17
Even better, with a Graphical User Interface: [GTKorphan](http://www.ubuntuforums.org/showthread.php?t=79028&highlight=gtkorphan).

---

### Post by dcstar on 2006-01-17
[QUOTE=niviche]Even better, with a Graphical User Interface: [GTKorphan](http://www.ubuntuforums.org/showthread.php?t=79028&highlight=gtkorphan).[/QUOTE]
Looks good, I wish the Debian site would let me download it!...   :(

---

### Post by bagel on 2006-01-18
Thanks alot, deborphan is doing exactly what I wanted!

Ciao, bagel

---

### Post by mcduck on 2006-01-18
You can also use deborphan with Synaptic, just make a new filter to show only orphaned packets :D

(I like to have only one app/task so managing all installs/uninstalls with Synaptic is nicer than having a separate GUI for removing orphaned packets)

---

### Post by tekwarren on 2006-01-18
Thanks for this tip, after creating a synaptic filter for only orphaned packages is there an easy way to uninstall? Or does each one have to be done individually?


(newb)

---

### Post by tekwarren on 2006-01-18
i might be doing this wrong but i made a filter in synaptic to only show orphaned by checking the box and when I use the filter it doesn't show anything does that mean there is nothing I can get rid of or am I doing something wrong :p

---

### Post by mcduck on 2006-01-18
that means that there are no orphaned packets on your system, but of course you can still uninstall programs that you don't need..

To make this clear, orphaned packet is something that is installed because some application you install needs it, but is not removed when you uninstall the original application.

And you don't need to select all packages one at time, select the first one, and then holding shift key click the last one and you can select them all to be removed at the same time ;)

---

### Post by tekwarren on 2006-01-18
Thanks for the explanation...that makes alot of sense since I really haven't installed much.

---

