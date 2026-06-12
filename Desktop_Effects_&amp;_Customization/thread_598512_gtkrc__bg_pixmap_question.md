---
title: "gtkrc : bg_pixmap question"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by oedipuss on 2007-10-31
I've got a gtk theme I want to modify, by adding a background pixmap to everything.

So, I've made a png image, and added the following to the 'default' style in the theme's gtkrc :
```
bg_pixmap[NORMAL]="myfile.png"
```

This works nicely, as every other style has a transparent background, except that I'd like the pixmap to stretch in one direction, along with the window, so its edges always coincide with the window edges, and repeat itself in the other, instead of it being cropped (if too big) or repeated in both axes. 
More specifically, I've got a 1024x50 pixmap, which I want to repeat vertically , and stretch horizontally.
Is there a way to do this ?

---

### Post by jsa on 2007-12-12
I'm sorry I can't help you, as I'm struggling with something similar too. I'd like to add a gradient background to the whole window. bg_pixmap tiles the image and I would like to stretch it. I also don't want the image to be cropped. I'm using pixmap engine with my theme and haven't found any reference to it supporting that kind of thing and neither do i know if any other engines support it. I would be really pleased if someone helped me out with this.

---

