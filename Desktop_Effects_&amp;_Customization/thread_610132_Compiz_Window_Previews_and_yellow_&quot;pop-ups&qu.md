---
title: "Compiz Window Previews and yellow &quot;pop-ups&quot;."
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by Ub1476 on 2007-11-11
When I put my cursor on the window tab, it shows the preview just fine, but it also shows the default "pop-up" (some sort of yellow background) which tells the name of the window. I wonder if there's anyway to remove this because the window preview already shows this in it's border (and it's written on the tab too..). 

Thanks in advance

---

### Post by Ub1476 on 2007-11-11
.

---

### Post by Ub1476 on 2007-11-12
.

---

### Post by Ub1476 on 2007-11-12
Any help please?:(

---

### Post by Zorael on 2007-11-12
Gnome or KDE? (Ubuntu or Kubuntu?)

You'll want to look into the settings of the taskbar to see if you can disable the tooltips there. Compiz can't quench them, as far as I'm aware.

The option exists in KDE at least, that much I know.

---

### Post by Ub1476 on 2007-11-12
Well, it's for Gnome..

I'll take a look into gconf (it's just so huge:o).

---

### Post by Ub1476 on 2007-11-12
Ok, I found it here in gconf: /apps/panel/global/tooltips_enabled

But it doesn't disable the tool tips for the windows (which is hat I want to remove in the first place), only other stuff like trash, volume etc..

---

### Post by Ub1476 on 2007-11-12
Yes, I fixed it! I went into compiz-config, General>Opacity, clicked on Add, wrote opacity with 0 values. Now it's there, but I can't see it!:)

---

