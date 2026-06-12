---
title: "Xubuntu 6.10 Hangs When I Log Out"
date: 2006-12-13
forum: Desktop Environments
---

### Post by Simon G Best on 2006-12-13
Hello!

I've just installed Xubuntu 6.10, and have encountered numerous problems.  One of them left me pressing my PC's hardware reset button!  That's something I really don't like to do.

The problem is this.  When I log out, it hangs.  I'm left with an empty screen (with blue background), a white pointer, and that's it.  The keyboard doesn't seem to do anything - even Num Lock's numb.  The pointer doesn't move when I move the mouse, the buttons do nothing, and Vulcan death grips (Ctrl-Alt-Delete) and the like are ineffectual.  That includes switching to virtual consoles - it just doesn't happen.  So hung my system appears to be, that I ended up hitting the reset button.

However, I also know that when ACPI is not disabled, pressing the power button on my PC leads the system to shutdown seemingly properly (instead of simply being immediately switched off).  But, because of what seems to be some sort of ACPI related bug (particularly keyboard problems), I've now got ACPI disabled.  As a result, I was left hitting the reset button.  I don't want to do that again.  (Fortunately, shutting down instead of logging out works.)

Would anyone be able to point me in the right direction towards a solution?

:)

---

### Post by tudawggz on 2006-12-13
You could try removing splash and quiet from your /boot/grub/menu.lst file so that it may show you the verbose linux messages as it is shutting down.  My system was hanging this morning on the stopping of my wireless card.

---

### Post by Simon G Best on 2006-12-13
> **tudawggz said:**
> You could try removing splash and quiet from your /boot/grub/menu.lst file so that it may show you the verbose linux messages as it is shutting down.  My system was hanging this morning on the stopping of my wireless card.

It's not hanging when I tell it to shut down (or reboot), just when I'm simply logging out (so that someone else could log in, for example).  Instead of returning to the graphical login thingy, it just hangs :(

---

