---
title: "unity up/down sliders"
date: 2016-12-20
forum: Desktop Environments
---

### Post by pete1977x on 2016-12-20
is there a way to widen the up and down sliders on the right side of screen in Unity?? I have the tweak tool..

---

### Post by howefield on 2016-12-20
You could try creating a file called gtk.css and place it inside the ~/.config/gtk-3.0 folder.

The contents could look like this

```
.scrollbar {
  -GtkScrollbar-has-backward-stepper: true;
  -GtkScrollbar-has-forward-stepper: true;
  -GtkRange-slider-width: 14;
  -GtkRange-stepper-size: 13;
}
```

Change the values to something bigger, say 20 or whatever suits you.

Going further you could copy the contents of the /usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css file to ~/.config/.gtk-3.0/ and play away.

---

