---
title: "[SOLVED] Theme not installing correctly?"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by flawedreality5 on 2007-08-31
Hey everyone. I installed Ubuntu again for the upcoming semester (I'm a CS major) and I need some help installing themes. I understand the difference between the different components of the theme and I think I'm installing them right. I drag and drop the theme files into the theme manager and it says they install correctly. I can see the option to use the theme under Controls and Window Border but they never display correctly. The buttons and scroll bar don't match the picture on gnome-look. They seem to revert to a default plain squarish theme. I've redownloaded them and tried to install a few times. The window border shows up when I select it but controls don't. I had this working last time I had linux installed and I thought I remember downloading something to get it to work but I don't remember. Thanks! :)

-Brandon

---

### Post by FuturePilot on 2007-08-31
Try this
```
sudo apt-get install gtk2-engines-pixbuf
```
Then reset your theme.

---

### Post by flawedreality5 on 2007-08-31
That's what it was! Thank you so much.

---

### Post by cudaman73 on 2007-08-31
Do you mind setting this thread to solved, then?

It should be under thread tools -> Mark as solved.

---

