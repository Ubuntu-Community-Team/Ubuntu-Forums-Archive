---
title: "Console problem"
date: 2005-11-11
forum: Desktop Environments
---

### Post by manobes on 2005-11-11
Hi all,

I have a wierd problem.  I don't use the text console too often, but today I hit ctrl-alt-f1 and noticed that the bottom few lines of the text console aren't displayed on my screen.  

That is, if I hit enter several times (23) I eventually lose sight of the prompt.  It's still "there" since typing exit logs me out, and typing clear clears the screen.  This is very puzzling.

Any ideas?

---

### Post by souki on 2005-11-11
I've seen that before with hoary on a widescreen
I don't remember exactly, but the framebuffer did not handle this resolution
I don't have this problem now with breezy

the only solution I've found for hoary, was to deactivate the splash mode in /boot/grub/menu.lst

---

### Post by manobes on 2005-11-11
[QUOTE=souki]the only solution I've found for hoary, was to deactivate the splash mode in /boot/grub/menu.lst[/QUOTE]

I take it removing the "splash" from this line will accomplish that?

kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash

---

### Post by souki on 2005-11-11
[QUOTE=manobes]I take it removing the "splash" from this line will accomplish that?

kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash[/QUOTE]

yes, all you need is to remove "splash"

if you want to keep your settings between kernel upgrade, you also have to modifiy this line

```
nonaltoptions=quiet splash
```

then reboot

---

