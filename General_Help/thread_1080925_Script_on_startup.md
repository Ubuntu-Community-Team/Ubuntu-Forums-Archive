---
title: "Script on startup"
date: 2009-02-25
forum: General Help
---

### Post by invincibletoviruses on 2009-02-25
how do i disable the script on startup that says "reading files needed to Boot" and it starts going through a list of "stuff"then my login comes up.

---

### Post by mb_webguy on 2009-02-26
If you're talking about what I think you're talking about, the best way to keep that from running is to not boot your computer, since that's actually your system starting up.

I don't think you shouldn't be seeing that, though, unless you've modified your GRUB menu.  In the terminal, type "sudo gedit /boot/grub/menu.lst" and look for this section:```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
Make sure the word "quiet" is on the defoptions line, as shown above.  Save and exit, then type the command "sudo update-grub" to update your GRUB menu.  If you still see all of that text the next time you reboot, then something else is going on, and you'll need to post a bit more detail to help us figure it out.

---

### Post by invincibletoviruses on 2009-02-26
i did as you told me, no result, i still see the *reading files needed to boot* script on start up.

---

