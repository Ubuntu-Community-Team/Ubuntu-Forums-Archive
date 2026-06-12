---
title: "Seg Fault on startup"
date: 2006-08-10
forum: Desktop Environments
---

### Post by the_duke_of_hazzard on 2006-08-10
I recently re-installed dapper to get wireless working. All was fine until I restarted this morning and received an error soon after boot: "Segmentation fault" repeated many times on the screen, followed by an error "/dev/hda5 does not exist" (or words to that effect).

It then put me into an ash terminal, part of the kernel I believe. So it doesn't get very far at all.

I might have done an upgrade from some new sources, but nothing out of the ordinary.

Is there any debug I can provide/perform to help me diagnose the problem?

---

### Post by stinerman on 2006-08-10
Segfaults that early in the boot process points to bad memory or a corrupt kernel image.

Try running the memtest.  I had a similar problem that the test caught.

---

### Post by the_duke_of_hazzard on 2006-08-11
Thanks for that - makes sense. Unfortunately memtest shows up nothing. Looks like I might have to reinstall :s

---

### Post by stinerman on 2006-08-11
You might want to try a reinstall of the kernel before you do that ...

---

