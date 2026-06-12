---
title: "Menu items not displaying properly"
date: 2012-10-21
forum: Desktop Environments
---

### Post by brickmack on 2012-10-21
I just upgraded from Ubuntu 12.04 to 12.10. Or some reason, menus (File, Edit, etc) aren't displaying properly. Specifically, the text is almost unreadable because it is nearly thesame color as the background (Though for some reason it acts differentlyfor different menus, as shown below. Pictures:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225867&stc=1&d=1350848341[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225869&stc=1&d=1350848341[/IMG]

This problem also exists with the buttons on notification dialog boxes, though I don't have a screenshot. Any suggestions on how to fix this? I'm running Unity on Ubuntu 12.10

---

### Post by paulmerchant on 2012-10-30
This was probably caused by some customizations to the Ambience theme. I had the same customizations as you to fix some problems with Java applications in 12.04.

If you still see this problem, check to see if you have a ~/.themes/Ambiance folder. If you do, rename it or move it (or delete it). 12.10 seems to have better menus out of the box.

---

### Post by greensaharatj on 2012-11-26
I am having this exact same issue...I can't seem to figure out what is causing this it just seems to happen out of the blue. Anybody else have an idea my home folder doesn't  have a ".themes" folder in it

---

