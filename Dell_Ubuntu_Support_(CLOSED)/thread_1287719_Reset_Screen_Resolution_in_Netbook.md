---
title: "Reset Screen Resolution in Netbook"
date: 2009-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Merk42 on 2009-10-10
So my brother went to increase the resolution on his Vostro A90 netbook.  Now he can't turn it back since the 'OK' button is off the screen.  I'm sure there's something to edit manually in the Xorg.conf, but as I don't have his netbook in front of me, and run Jaunty (he runs Hardy) I'm not sure what part to change.

---

### Post by jeremyswalker on 2009-10-10
One way to get the OK button back on the screen is to hold down the 'Alt" button and drag the window. I've had to do this in the past, as well.

---

### Post by Merk42 on 2009-10-10
> **jeremyswalker said:**
> One way to get the OK button back on the screen is to hold down the 'Alt" button and drag the window. I've had to do this in the past, as well.

I told him about that, but he said it wouldn't work.

---

### Post by ugm6hr on 2009-10-12
> **Merk42 said:**
> I told him about that, but he said it wouldn't work.

Wouldn't work or doesn't work?

Because it does (or should) allow the window to be placed anywhere.  You just have to "grab" the window somewhere near the bottom (i.e. not on the title bar) with Alt held.

But actually, rather than an xorg edit, it may be easier to use:
```
sudo apt-get install xrandr
sudo xrandr -q
sudo xrandr -s 1024x600
```

I haven't used Hardy / the Dell Ubuntu for a few months, but I think that should work.

---

