---
title: "how do i get menu like this?"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by Villenya on 2007-11-02
[http://farm2.static.flickr.com/1249/1408476003_f72755aef7_o.png](http://farm2.static.flickr.com/1249/1408476003_f72755aef7_o.png)

how can i make the main menu transparent? I can make it transparent through compiz-fusion opacity setting but sadly that makes all the icons and my awn dock transparent also.

p.s. what theme is he using?

---

### Post by Baby Boy on 2007-11-02
Right-click the panel
Select *Properties*
Select the *Background* tab
Move the slider next to *Style* to the far left (Transparent)

---

### Post by VictorR on 2007-11-02
If you are talking about the menu on the top, then just right-click on it, select Properties -> Background -> Solid Color, black and opacity about 60%. It affects only menu background.

---

### Post by Villenya on 2007-11-02
tnx for the quick reply.

The problem with your method is that only segments of the main menu are transparent. Other segments such as the clock, system monitor, system tray are still solid.

---

### Post by Baby Boy on 2007-11-02
> **Villenya said:**
> tnx for the quick reply.

The problem with your method is that only segments of the main menu are transparent. Other segments such as the clock, system monitor, system tray are still solid.
That's where Compiz Fusion jumps in. 

*Alt+mouse wheel* changes opacity - try it on the parts you've mentioned.

EDIT: Also, take a look at [this]("http://ubuntuforums.org/showthread.php?t=589127") HOWTO.

---

### Post by KingWilliam on 2007-11-02
> **Baby Boy said:**
> 
*Alt+mouse wheel* changes opacity - try it on the parts you've mentioned.


Thats good to know :D thx!

---

### Post by VictorR on 2007-11-02
I had this problem with one GTK2 theme. The gtkrc file has some settings, which affect the gnome panel as well. I don't know (yet) what should be changed to prevent this, but maybe soon I will find this out, as I am working with modification such a theme.
If you are going to set transparency for the panel through Compiz Settings this could help:
type:  DOCK
name:  gnome-panel
class: Gnome-panel
title: Top Expanded Edge Panel
xid:   0xa00001
Ignore xid, it can be different.

---

