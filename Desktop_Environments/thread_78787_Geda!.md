---
title: "Geda!"
date: 2005-10-18
forum: Desktop Environments
---

### Post by antdengineer on 2005-10-18
So whats with the geda packages in the breezy repos.  They dont work.  I installed all of them but when I run geda none of the commands in the menus work.  No schematic editor or anything.  When I try to select the schematic editor i get this spitting out in the terminal:confused:

```
gEDA/gschem version 20040111
gEDA/gschem comes with ABSOLUTELY NO WARRANTY; see COPYING for more details.
This is free software, and you are welcome to redistribute it under certain
conditions; please see the COPYING file for more details.

Error : system-error [C:52 L:25] in /etc/gEDA/system-gschemrc
Most recently read form: (#@load (#@string-append #@gedadatarc /system-commonrc))
Failed to read init scm file [(null)/gschem.scm]

```

---

### Post by thevoice on 2005-10-19
I'm having exactly the same problem.  Anyone have any ideas?

---

### Post by antdengineer on 2005-10-20
Well, can anyone at least recomend the best way to do logic design on a linux system? Whats the best software to use?

---

### Post by Ampersand on 2005-10-20
I found klogic quite good for logic design, it might be worth going through the electronics and electronics (universe) sections in Synaptic, and trying out a few of them to see what does what you want it to.

---

### Post by thevoice on 2005-10-21
Looks like I'll be compiling from source, I need to use geda to share work with a friend.  Ho hum.

---

### Post by gradedcheese on 2005-10-22
did anyone, by chance, find a solution to the broken geda packages?  I'd really like to run gschem.  I tried grabbing a new system-gschemrc file from the geda website but that didn't help.  Line 25 is in bold:

; Load up gafrc
;
; Contains paths needed for all gaf programs
(define gedadata (getenv "GEDADATA"))
(define gedadatarc (getenv "GEDADATARC"))
**(load (string-append gedadatarc "@PATHSEP@system-gafrc"))**

---

### Post by daller on 2006-02-15
The bug has been reported here:

[https://launchpad.net/distros/ubuntu/+source/geda-gschem/+bug/4440](https://launchpad.net/distros/ubuntu/+source/geda-gschem/+bug/4440)

...Let's hope that is works in Dapper - I kinda NEED this app!

---

### Post by ancient_ee on 2006-03-04
I tried to install GEDA on ubuntu, but gave up after a successful (debian pkg) install because it would not run. The error message "horizontal scrolling not enabled" was much too cryptic for me, a linux newbie. GEDA was/is my main motivation for learning linux, so I blew away my ubuntu and installed straight debian. It was a difficult intstall (I had to edit text config file for it to detect my PS2 mouse to run X windows), but then GEDA installed and is now working perfectly. So now you have one solution/success story. Good luck.

---

