---
title: "MATE Clock-applet text color white"
date: 2019-09-10
forum: Desktop Environments
---

### Post by validust on 2019-09-10
Hi y´all!
Having upgraded to ubuntu-18.04, I saw that my preferred theme GreenLaguna showed only black text in the top panel (uppermost img).
1fallen´s /gtk.css , placed in the home-folders .config/gtk-3.0 , made the middle icon´s text white (second img). 
After a number of hit-and-misses, I happened upon an expression that made the menu bar white (third img).
But the clock applet stays black. If any one knows the kind of magic that changes it to white, I´d very much like to see it! 
For now I´ve made a light square on the background. It works...so-so (lowermost img). The gap between the clock applet and the volume icon is *sometimes* occupied 
by the battery monitor icon ;)

Edit 8/3 2020: Found the magic. The gtk3/gtk.css file now makes also the clock applet text white.


This is how my gtk.css file looks:

```
panel-toplevel.background.horizontal,
.mate-panel-menu-bar menubar > menuitem {
    text-shadow: none;
    padding: 3px 5px;
    color: white;
}

.mate-panel-menu-bar  {
    color: white;
}

#clock-applet-button.flat.toggle > box.horizontal > label {
    font-weight: normal;
    text;
    color: white;
}

```

My machine: Dell Latitude E7470

---

