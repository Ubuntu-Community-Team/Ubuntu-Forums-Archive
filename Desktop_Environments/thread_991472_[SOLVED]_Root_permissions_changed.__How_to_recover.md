---
title: "[SOLVED] Root permissions changed.  How to recover?"
date: 2008-11-23
forum: Desktop Environments
---

### Post by roadrawts on 2008-11-23
I accidentally changed permissions in / to 744.  I thought I was in a different directory.  Now everything is blank.  How can I recover from this dumb move?

---

### Post by psusi on 2008-11-23
I don't know what you mean by "everything is blank" but just chmod it back.

---

### Post by sisco311 on 2008-11-23
if you changed the permissions recursively(chmod -R ...), then backup your data and reinstall ubuntu.

if not, then boot a live cd, mount the partition and restore the permissions to 755:
```
sudo chmod 755 */mount/point*
```

---

### Post by roadrawts on 2008-11-23
> **psusi said:**
> I don't know what you mean by "everything is blank" but just chmod it back.
I can't get to a terminal from rebooting.  The screen is just blank when I reboot.  ESC doesn't do anything. CTL-ALT-F1 doesn't do anything either.  Do I have to boot from a CD?

---

### Post by roadrawts on 2008-11-23
I'm downloading a live cd on another computer.  But isn't there a keyboard sequence that will bring me into terminal mode from 8.04?  Earlier versions of Ubuntu let me do that.

---

### Post by sisco311 on 2008-11-23
> **roadrawts said:**
> I'm downloading a live cd on another computer.  But isn't there a keyboard sequence that will bring me into terminal mode from 8.04?  Earlier versions of Ubuntu let me do that.

Try to press Ctrl+Alt+F2 to swith to the virtual terminal.

Or try to reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

In the root shell type:
```
chmod 755 /
reboot
```

---

### Post by roadrawts on 2008-11-23
Ok. Thank you all.  I can't get ESC to work to get me into the GRUB menu.  Don't know what's wrong.  I'll just keep plugging away.

---

