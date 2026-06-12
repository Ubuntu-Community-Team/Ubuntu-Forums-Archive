---
title: "gdm crashes"
date: 2010-03-18
forum: Desktop Environments
---

### Post by denarced on 2010-03-18
I have 64-bit ubuntu 9.10
I think I updated my linux kernel

And after that grub blinks.
I think everything is there like it's suppose to be.
Windows 7 is there and starts up normally.
But ubuntu and gdm starts normally for a while and you can see the black and white ubuntu logo but then it just drops you into text-only screen where it reads: "Ubuntu 9.10 computer_name tty1
computer_name login:"

I logged in, tried : startx => it says no such program.
Tried sudo gdm => sudo: gdm: command not found

Please help me with this one

Also tried sudo update-grub =>no such command
My normal files are there though

---

### Post by phildini on 2010-03-19
Are the entires for the old kernel still in GRUB, and can you boot from them to access GDM correctly?

---

### Post by denarced on 2010-03-19
Yeah, tried other kernel entries too
No go with 'em
Can't try stuff anymore
Took one of my backups and got my system working again

---

### Post by denarced on 2010-03-20
I'd say these types of problems are hard to diagnose since people don't wait around for help with their primary systems, they need to use 'em. All the time. So it's re-install or backups pretty soon.

---

