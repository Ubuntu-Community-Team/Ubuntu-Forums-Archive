---
title: "Make Windows the Default OS w/ GRUB"
date: 2005-12-26
forum: General Help
---

### Post by TheSe7enthProphet on 2005-12-26
Ok, I know where the GRUB menu is on my Ubuntu Hard Drive, and I know how to open it as the root, but all I need ot know is how I make it so that Windows is the first to load rather than Linux.

Why? I am not the only person to use this computer, but I am the only person that uses Linux. This causes problems when the power goes out and it automatically goes to Linux; especially because the people in this household have not a clue how to get back to Windows. Thanks.

---

### Post by pharcyde on 2005-12-26
Modify the /boot/grub/menu.lst

look for the command "default X" where X is the number of the entry starting at 0 that you want to boot by default.  0 is the first entry, 1 is the next, etc.

My linux partion is 0 and my windows is 1 so if I wanted to boot windows I would change the entry to "default 1"

---

### Post by Sutekh on 2005-12-26
Yep start counting from 0 up until the entry for Windows.  Check out your /boot/grub/menu.lst, and count up every time you see 'title'.  This includes 'Other Operating Systems'.

---

