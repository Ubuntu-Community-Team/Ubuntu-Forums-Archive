---
title: "restoring menu.lst"
date: 2009-01-29
forum: General Help
---

### Post by Ace_NoOne on 2009-01-29
During the kernel upgrade (2.6.27-11) this morning, I failed to accept the updated *menu.lst* - and don't know how to revert that decision now.

Since I'd customized my */boot/grub/menu.lst* (removed *quiet* options), I was prompted for what to do - and accidentally chose the shell option. Since I wasn't sure what to do, I just typed *exit* - which apparently resulted in me keeping the current *menu.lst*, which is missing the entry for the latest kernel.

I suppose I could just duplicate my existing entries and replace *-9* with *-11* - but I'm not entirely sure about that (e.g. what about the UUID).

Any help would be appreciated!

---

### Post by jerome1232 on 2009-01-29
Issueing a ```
sudo update-grub
```
should do the trick, btw if you change your options near the top of menu.lst where all the comments are, grub will reflect your changes through that auto update process.

For instance mine looks like this
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792

```

---

### Post by sisco311 on 2009-01-29
never mind

---

### Post by lefocus on 2009-01-29
test

---

### Post by Ace_NoOne on 2009-01-29
Thanks for the quick responses!

> **jerome1232 said:**
> Issueing a ```
sudo update-grub
```
should do the trick
Indeed it did - I'm all set now.

> **jerome1232 said:**
> btw if you change your options near the top of menu.lst where all the comments are, grub will reflect your changes through that auto update process.
> **sisco311 said:**
> Just replace the version number in the title, kernel and initrd lines. And use the same uuid.
That's very useful information - much appreciated!

PS: I can't seem to mark this thread as solved, as described in sisco311's sig!?

---

### Post by jerome1232 on 2009-01-29
it's been temporarily removed, the forums were getting heavy database corruptions issues and it was part of the cause I guess.

---

