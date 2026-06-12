---
title: "Help With Theme - Selection Color"
date: 2011-07-11
forum: Desktop Environments
---

### Post by zerginale on 2011-07-11
Hello, great Ubuntu people!
I've need some help here. [Here's a picture](http://noob.hu/2011/07/11/help_0.png), and here's what I need:
I want the orange selections (the selection made with the cursor too) to be another color. I've tried to modify it by the gtkrc and from the menu too, but I couldn't manage it to work.
The theme is New Wave.
Any thanks would be greatly appreciated!

PS: my OS is Ubuntu 10.04 LTS.

---

### Post by Krytarik on 2011-07-11
Unfortunately, the "New Wave" theme is pixmap based. So, you can well forget it, unless you are eager to modify all concerning images. ;-)

Greetings.

---

### Post by mcduck on 2011-07-12
> **zerginale said:**
> Hello, great Ubuntu people!
I've need some help here. [Here's a picture](http://noob.hu/2011/07/11/help_0.png), and here's what I need:
I want the orange selections (the selection made with the cursor too) to be another color. I've tried to modify it by the gtkrc and from the menu too, but I couldn't manage it to work.
The theme is New Wave.
Any thanks would be greatly appreciated!

PS: my OS is Ubuntu 10.04 LTS.

You mean the box that is drawn when selecting items from desktop or a file manager window?

Just edit the theme's gtkrc file (in /usr/share/themes/New Wave/gtk-2.0/gtkrc) and change the color on the "NautilusIconContainer::selection_box_color" (line 128 of the file).

You'll need to reload the theme afterwards to see the changes. Either log out and back again, or switch to another theme and then back to New Wave.

---

### Post by zerginale on 2011-07-12
Thank you very much, it's working now. :D
Krytarik: I've already recolored all of the images.

---

