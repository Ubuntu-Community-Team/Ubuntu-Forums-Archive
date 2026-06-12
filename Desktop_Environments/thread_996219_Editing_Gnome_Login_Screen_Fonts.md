---
title: "Editing Gnome Login Screen Fonts"
date: 2008-11-28
forum: Desktop Environments
---

### Post by klausner on 2008-11-28
The username field of my login screen started showing all the input as a box character. Since I knew this wasn't standard, I figured it must be a font problem.

I decided to edit /usr/share/gdm/themes/*[myaplash]*/layout.xml. But when I opened the file, I couldn't identify which font line controlled the username field. So after making a backup of the file, I did a global change on the font types to Verdana. 

This solved the problem, and so encouraged I decided to see if I could find a font I liked better. At this point I found that I had mistyped Verdana as Verdna, a font not present on my system.

What I found was that if I typed in a legitimate font name, I get boxes for the input. If I use a garbage name, I get the actual input text.

So I clearly don't understand what I'm doing. Anyone have an explanation?

---

### Post by klausner on 2008-12-06
Bump

---

### Post by klausner on 2008-12-12
Bump.

---

### Post by klausner on 2008-12-20
Bump. Surely someone has an answer for this.

---

### Post by klausner on 2009-01-25
Bump!

---

