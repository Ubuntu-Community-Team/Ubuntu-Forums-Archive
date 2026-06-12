---
title: "GRUB Error 22"
date: 2009-01-25
forum: General Help
---

### Post by Jaded Misanthrope on 2009-01-25
Recently, I wasn't concentrating and I ended up deleting my Ubuntu partition that I had dual-booted with Vista. Whenever I try to boot into Vista now, I get the message

'Grub Loading stage 1.5...

Grub Loading, please wait...
Error 22'

I seem to remember reading that using the Vista recovery disk, entering the command console and running the 'fixmbr' command would alleviate this, so I downloaded the recovery disk, select the option to enter the console and try to run fixmbr but I am told that it is not a valid 'batch file, command or internal or external program' (or words to that effect). What can I do to just have Vista work -- essentially, to remove GRUB and just automatically boot into Vista.

---

### Post by caljohnsmith on 2009-01-25
From the Vista CD, instead try:
```
bootrec /fixmbr
```
The geniuses at Microsoft of course have to change the command between Windows versions just to make it fun for the rest of us.

---

