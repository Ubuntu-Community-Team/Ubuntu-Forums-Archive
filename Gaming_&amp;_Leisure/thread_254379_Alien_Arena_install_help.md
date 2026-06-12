---
title: "Alien Arena install help?"
date: 2006-09-09
forum: Gaming &amp; Leisure
---

### Post by forcesofhabit on 2006-09-09
I've download the .run file. I tried some installation methods I found in the forums of the AA website. I don't think I'm doing this right... can someone give me step by step instructions?

~Noob

---

### Post by fotion on 2006-09-09
> **forcesofhabit said:**
> I've download the .run file. I tried some installation methods I found in the forums of the AA website. I don't think I'm doing this right... can someone give me step by step instructions?

~Noob

more info might be nice.

but with a .run file it should be straight forward.

open terminal

**cd /dir_containing .run file**

the execute .run file

**./whatever_version_of_alienarena.run**

after that a nice little gui installer should pop up. if it does not the terminal should have more information containing the errors.

if it's just that a menu item wasn't created then open a terminal and type:

** cd /home/your_username/alienarena2006**

then

**./AlienArena**

Good Luck

---

### Post by forcesofhabit on 2006-09-09
"bash: ./alienarena-2007-x86.run: Permission denied"

Why is this?

---

### Post by fatsheep on 2006-09-09
Make sure your file has permission to execute:

Right click on the file, go to properties, then select permissions.   Now makes sure the "read", "write", and "execute" boxes for "owner" are checked.

---

### Post by fotion on 2006-09-09
is it executable?

to make executable open terminal and type:

**chmod +x alienarena-2007-x86.run**

---

