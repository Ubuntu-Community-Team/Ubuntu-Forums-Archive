---
title: "is it possible to install both firefox 2.0 and firefox 3.0"
date: 2008-12-08
forum: General Help
---

### Post by SoDanishWasLike on 2008-12-08
Hey guys,

My work website that I log into only supports up to firefox 2.0

Is it possible to have a system running both firefox 2.0 AND firefox 3.0? I use firefox 3.0 already and don't want to downgrade to firefox 2.0 for personal use.

FYI - I already tried installing the firefox-2 package in synaptic package manager but when I ran it I guess it was using the firefox-3.0 kernal cause firefox 3.0 would always run. I've also tried running firefox 2.0 by hitting alt-f2 and typing in "firefox"

My work website only supports IE6 and Firefox 2.0 so using Opera or Epiphany for work is out

Please Help!
Danish

---

### Post by gettinoriginal on 2008-12-08
You may want to read this:

[http://ubuntuforums.org/showthread.php?t=837016](http://ubuntuforums.org/showthread.php?t=837016)

---

### Post by Meow27 on 2008-12-08
you can compile firefox 2 in a folder and run it from there (it would be tedious but since it would be only installed in the folder, it will not conflict with any other program you have)

(compiling from the source code that is)

---

### Post by SoDanishWasLike on 2008-12-09
> **gettinoriginal said:**
> You may want to read this:

[http://ubuntuforums.org/showthread.php?t=837016](http://ubuntuforums.org/showthread.php?t=837016)

Thank You!

This worked. All I had to was run firefox but with a modified command forcing it to a certain profile, such as:

firefox -P default
firefox-2 -P work

Of course, life isn't fair and the work site still didn't work. I think VirtualBox is in my future....

---

