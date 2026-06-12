---
title: "Gnome 3.2, change font color on panel"
date: 2011-11-29
forum: Desktop Environments
---

### Post by cortman on 2011-11-29
So I've tried a number of things so far and none seem to work.
I'm using the MetalX theme in Gnome 3.2, and I really really like it, except that the clock and widgets on the panel are all a very slightly darker grey than the panel itself. I'd like to change these to black.
I tried going into home/user/.themes/MetalX and editing the .css file, but it doesn't seem to work.

---

### Post by thongstele on 2011-11-29
> **cortman said:**
> So I've tried a number of things so far and none seem to work.
I'm using the MetalX theme in Gnome 3.2, and I really really like it, except that the clock and widgets on the panel are all a very slightly darker grey than the panel itself. I'd like to change these to black.
I tried going into home/user/.themes/MetalX and editing the .css file, but it doesn't seem to work.

Please open the file gnome-shell.css in /home/user/.themes/theme_name or /usr/share/themes (with root) and search for ".panel-button". 

.panel-button {
    -natural-hpadding: 6px;
    -minimum-hpadding: 4px;
    font-weight: bold;
    **color: #657383;**
    text-shadow: black 0px 1px 1px;
    transition-duration: 300;
}

you could change the text (and icon) color on top bar panel by changing the color code as above. Google for which color code you want to adapt with your theme.

---

### Post by cortman on 2011-11-29
Aha! Finally found it! Now I know how stout Cortez must have felt, when with eagle eye he star'd at the Pacific, and all his men... er, anyway. It worked! Thanks so much!

For anyone else referencing this, I tried a editing the gnome-shell.css file in /usr/share/gnome-shell/theme, and that didn't do it. Going to /home/user/.themes/theme_name/gnome-shell.css and changing that changed it.

```


.panel-button {
    padding: 0px 12px;
    font-weight: bold;
    color: <b>black</b>;
    transition-duration: 100;
}

```

---

