---
title: "Removed from sudoers file !?"
date: 2009-03-01
forum: General Help
---

### Post by furry_freak on 2009-03-01
I somehow managed to get removed from the sudoers file without (knowingly) doing anything. The only thing that i think could have caused it was adding myself to the 'disk' and 'vboxusers' groups like so:
"sudo usermod -G disk,vboxusers rob". I don't see why that would've done it, but besides that all I did all day was listen to music and install windows 2k in virtual box.

The problem is, if I'm not in the sudoers file, how can I add myself back to it without using sudo?

---

### Post by prinny42 on 2009-03-01
Do you have a live CD lying around?  With that you'll automatically have root privileges, so you can mount your hard drive and edit sudoers manually.  Even if you don't have one, I don't think any of the stuff you need to do to make one requires privileges.

By the way, yeah, the problem was that command.  If you want to append groups, use the -a option too; the -G option alone will not only add you to the groups listed, but remove you from the groups not listed.

---

### Post by Nepherte on 2009-03-01
Just boot your computer using the recovery entry in the grub boot menu. Then add yourself to the admin group again.

---

### Post by lswb on 2009-03-01
When first booting your computer a stock install has an option in the grub menu for "recovery mode" You may need to press the escape key during boot to make the menu visible. Select the recovery mode option and then "root shell" from the short menu that appears.

---

