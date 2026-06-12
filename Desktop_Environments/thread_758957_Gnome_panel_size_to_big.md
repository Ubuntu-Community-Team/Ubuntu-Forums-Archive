---
title: "Gnome panel size to big"
date: 2008-04-18
forum: Desktop Environments
---

### Post by fbn on 2008-04-18
Hi,

I've changed the gtkrc in /usr/share/themes/Human/gtk-2.0 to get smaller icons in the Gnome menu, which works fine.

But the Gnome panel is still too big (height). I've configured it to be 18 pixels but it's still the same as 24 pixels.

How can I get the Gnome panel smaller?

This is what I have in gtkrc:

gtk-icon-sizes = "panel-menu=16,16:gtk-menu=16,16:gtk-button=16,16:gtk-small-toolbar=16,16:gtk-large-toolbar=24,24:gtk-dialog=32,32:gtk-dnd=32,32

---

### Post by Sam Lars on 2008-04-18
If you right click on the panel and open the preferences window, it doesn't let you go smaller than that.

---

### Post by fbn on 2008-04-19
No it won't. I've set it to 18 pixels which is the smallest value.

But it wont get smaller than 24 pixels actually, even if I set it to 20, 18 or whatever.

It's like an icon is 24 pixels in size and therefore the panel won't get smaller because the icon won't fit. Have you tried on your machine?

---

### Post by Sam Lars on 2008-04-19
Yes, it goes to 23 and will not let me get smaller.  Maybe it has to do with screen resolution?  I have 1280x1024.

---

### Post by fbn on 2008-04-19
I don't think so. If you create a new panel with nothing on it, you can resize it smaller.

---

### Post by Sam Lars on 2008-04-19
I tried that and it still won't go smaller.

---

### Post by fbn on 2008-04-19
is it completely empty?

---

### Post by bmac on 2008-04-19
I believe the min. panel size is also related to panel font size. Try changing your panel font size (smaller), then try and reduce the panel pixel size..

---

### Post by fbn on 2008-04-19
already done that. the font is smaller than the panel, it's actually smaller than the ubuntu icon of the menu. other suggestions? does it work for you?

---

### Post by Sam Lars on 2008-04-19
bmac is correct, by setting a smaller application font, which applies to the panel, I was able to go down to 16 or so, and it did actually change all the way.

---

### Post by fbn on 2008-04-19
not working here, font is really small but panel is way bigger

---

### Post by Sam Lars on 2008-04-19
I do think that the panel may be way bigger than the font size is.  You might want to file a bug if you think that the panel size should truly be allowed to be smaller.

---

### Post by jagrav on 2008-05-03
> **fbn said:**
> not working here, font is really small but panel is way bigger

I am having the same problem after upgrade to Hardy Heron. Tried the suggestions given here with no effect.

---

### Post by fbn on 2008-05-04
Hi, please confirm / comment this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/223075](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/223075)

---

### Post by jagrav on 2008-05-04
Bug report confirmed.

---

