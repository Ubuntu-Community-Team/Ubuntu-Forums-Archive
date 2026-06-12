---
title: "How to create desktop shortcut for running a command?"
date: 2009-03-26
forum: General Help
---

### Post by Sorrakritch on 2009-03-26
How to create desktop shortcut to run a command as below?

sudo $HOME/ldoce/ldoce

Please help

---

### Post by pennacook on 2009-03-26
You can just right click in the desktop and create a new launcher with this command in it.

---

### Post by CatKiller on 2009-03-26
You're going to have to use **gksudo** rather than **sudo** in your command (or **kdesu** if you're using Kubuntu), since otherwise there will be no way for you to put your password in. Out of interest, why are you using sudo for something that's in your Home folder anyway?

---

### Post by Sorrakritch on 2009-03-27
:KS Great Thanks.. That works for me (using "kdesu" under kubuntu)

By the way, under Thread Tools, I can find only these options:
 - Show Printable Version
 - Email this Page
 - Subscribe to this Thread
 - Add a poll to this Thread

But no "Solved" option to be selected as advised :confused:
SRK

---

### Post by aeiah on 2009-03-27
> **Sorrakritch said:**
> 
By the way, under Thread Tools, I can find only these options:
 - Show Printable Version
 - Email this Page
 - Subscribe to this Thread
 - Add a poll to this Thread

But no "Solved" option to be selected as advised :confused:
SRK

it got removed, along with the thanks button i believe.

---

### Post by CatKiller on 2009-03-28
> **Sorrakritch said:**
> no "Solved" option to be selected as advised

Ah. Yeah, hadn't been here for a while. Guess I'd best change my signature then, really...

Ta.

---

