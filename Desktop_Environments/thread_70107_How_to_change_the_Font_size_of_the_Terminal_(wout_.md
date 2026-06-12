---
title: "How to change the Font size of the Terminal (w/out GUI)"
date: 2005-09-28
forum: Desktop Environments
---

### Post by Son Volt on 2005-09-28
When I hit cntrl-alt-F1 to switch run levels to a basicl command prompt, the font size is way too large. How can I adjust these settings since they aren't part of the graphical desktop environment?

---

### Post by tonym on 2005-09-29
Add vga=ask to your kernel boot parameters.  When you boot you will then be given various choices for screen layout.  When you have found the one you like replace "ask" by the specified value.

Regards

Tony.

---

### Post by Son Volt on 2005-09-29
[QUOTE=tonym]Add vga=ask to your kernel boot parameters.  When you boot you will then be given various choices for screen layout.  When you have found the one you like replace "ask" by the specified value.
Regards
Tony.[/QUOTE]



How exactly do I access the kernel boot parameters? Is there a config file I'm looking for?

thanks!

---

### Post by tonym on 2005-09-29
Edit /boot/grub/menu.lst

Look for a line like 
# kopt=root/dev/hda1 ro
It may have other parameters.

Add vga=ask to the end of this line

After saving call update-grub and reboot

---

### Post by Son Volt on 2005-09-29
[QUOTE=tonym]Edit /boot/grub/menu.lst
Look for a line like 
# kopt=root/dev/hda1 ro
It may have other parameters.
Add vga=ask to the end of this line
After saving call update-grub and reboot[/QUOTE]


Ok I did what you said and when I rebooted, it asked me to pick a vga-mode - with options like
Columns x Rows
80x25
80x45
etc

I just picked one and nothing appeared to change when it booted up.

---

### Post by Son Volt on 2005-09-30
Whao, the edit box I'm typing in is growing if I put my mouse over the editing icons. WTF is up with that?

---

