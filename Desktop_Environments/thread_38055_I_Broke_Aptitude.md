---
title: "I Broke Aptitude"
date: 2005-05-29
forum: Desktop Environments
---

### Post by kvidell on 2005-05-29
Ugh.

So, apparently, I can click on things in my xterms because I installed gpm.
So I had aptitude open and accidentally double clicked on the "Admin" section... Now everything in that section is marked for removal.
How do I undo this? Of course closing the app and opening it again doesn't fix the problem, it remembers my choices.

Anyone know of a fix? This really sucks.
- Kev

---

### Post by joshmachine on 2005-05-30
Try running aptitude highlight the "Installed packages -> admin" entry and type 
"+"  (i.e. Shift and the +/= key)

This marks these packages for installation (since they are already installed they will just be unmarked for removal.)

In aptitude your selections on organizational containers are propagated down to the packages they contain.  you probably accidentally typed "-" (remove) or "_" (purge) on the admin section.

Cheers,
Josh

---

### Post by kvidell on 2005-05-30
[QUOTE=joshmachine]Try running aptitude highlight the "Installed packages -> admin" entry and type 
"+"  (i.e. Shift and the +/= key)

This marks these packages for installation (since they are already installed they will just be unmarked for removal.)

In aptitude your selections on organizational containers are propagated down to the packages they contain.  you probably accidentally typed "-" (remove) or "_" (purge) on the admin section.

Cheers,
Josh[/QUOTE]
 Oh awesome :) Thank you very much!
It ends up that I marked everything for removal :P great. I just did your trick at the root entry for "Installed Packages" and all was well.

Thank you again!
- Kev

---

