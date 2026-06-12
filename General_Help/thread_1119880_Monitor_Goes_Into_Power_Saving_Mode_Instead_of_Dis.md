---
title: "Monitor Goes Into Power Saving Mode Instead of Displaying Boot Loader"
date: 2009-04-08
forum: General Help
---

### Post by ddarkjedie on 2009-04-08
The title says all.

I'm running 8.10, and I've always had this problem.

The question is, how do I fix it?

Oh, but I might note that when I use a live CD, the boot loader is displayed.

---

### Post by ddarkjedie on 2009-04-08
Come on!  I need some help here!

---

### Post by ddarkjedie on 2009-04-10
Oh, whoopie!  No one is posting!

---

### Post by lisati on 2009-04-10
Hi. Your question has been spotted.
Sometimes a tweak to the menu.lst settings can help. Have a look in /boot/grub/menu.lst for a line that reads something like this:
> # defoptions=quiet splash
One of the options you can add is to specify which video mode to use.

---

