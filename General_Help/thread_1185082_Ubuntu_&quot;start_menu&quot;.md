---
title: "Ubuntu &quot;start menu&quot;"
date: 2009-06-11
forum: General Help
---

### Post by the_monster on 2009-06-11
Where is the ubuntu "start menu" stored. I would like to be able to back it up after I make mods to it.
Thanks.

---

### Post by drs305 on 2009-06-11
This is probably the one you are asking about:
What OS/Kernel gets booted: /boot/grub/menu.lst

Other important system files:

What folders get mounted where:  /etc/fstab

What repositories are checked when you run an update request: /etc/apt/sources.list

If you are asking about something else, like the Applications, Places, System menus, please clarify your request.

---

### Post by the_monster on 2009-06-11
Yes Applications.

---

### Post by ad_267 on 2009-06-11
Any modification you make to the menus are stored in ~/.local/share/applications I think.

---

### Post by the_monster on 2009-06-16
Thanks for the information!

---

