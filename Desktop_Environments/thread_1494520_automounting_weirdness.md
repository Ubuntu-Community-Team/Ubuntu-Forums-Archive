---
title: "automounting weirdness"
date: 2010-05-27
forum: Desktop Environments
---

### Post by slumbergod on 2010-05-27
I've looked through the forums and the only people who seem to be having auto-mounting issues are people with a floppy enabled in their bios or auto-login enabled. Neither of these apply to me.

I am having strange issues since the proposed updates came through to fix the thunar bug where it was not possible to browse in detailed view.

Since those updates, USB flash drives no longer automount. Same for data dvds. I have tried disabling then re-enabling and no success. Everyone else who applied the updates for the thunar bug reports no problems so I am at a loss.

If I insert a USB flash drive the following happens:
- I get the icon for it in Places
- I get the desktop icon for it
- it appears in the shortcuts pane in thunar

But it is not mounted. I have to do that manually. Then there is the really weird thing...when I go to remove it by right clicking...
- in Places, it says unmount
- on the Desktop the icon says unmount
- in Thunar it says Eject (no unmount option).

There are no fstab entries. Gnome services are being loaded at boot. But something still appears to be buggy in xubuntu.

Anyone else experiencing this or seen an explanation for it?

---

### Post by slumbergod on 2010-05-28
Much to my relief after an entire afternoon's investigation, I discovered that a ppa I had added to update some xfce packages had left my system with a mish-mash of clashing versions. ppa-purge restored the packages back to their originals then proposed updates updated them to the latest versions which included bug fixes.

It was a nice learning experience which has shown me just how useful ppa-purge is.

---

### Post by teedubb on 2010-05-29
not sure i fully understand your solution, could you post more detail because i'm having the same issue and i use thunar as well.

---

