---
title: "White Progress Bar on Feisty using Simple Theme"
date: 2007-05-29
forum: Desktop Environments
---

### Post by themeone on 2007-05-29
I'm using the same theme in Feisty as I did with Dapper (Simple with Mist window border).  In Dapper I got the normal dark blue on grey progress bar in Firefox and for downloading system updates.  Now in Feisty the progress bar is white.  White on grey isn't that easy to see!

It makes no difference whether my default depth in xorg.conf is set to 16 or 24.

My graphics driver is i810, but I get the same problem on another computer using a different graphics card.

I've had a look at this file:

/usr/share/themes/Simple/gtk-2.0/gtkrc

and got a blue progress bar by changing engine from "thinice" to "mist" or "clearlooks" but both make other parts of the desktop look ugly.

Is there anything else I can do?

---

### Post by mcduck on 2007-05-30
check that you have all GTK2-engines installed (including the pixbuf engine)

---

### Post by themeone on 2007-05-30
gtk-2-engines-pixbuf was already installed, though gtk-engines-pixbuf wasn't.  I installed it, along with all the other gtk2-engines, and also gtk-engine-thinice (since this is the engine my theme appears to use) but I still get the white progress bar.

---

### Post by 81golfcaddy on 2007-05-31
I also have the same problem. while downloading or anything that has progress. you dont know where it is as far as %

---

### Post by themeone on 2007-06-02
I found a satisfactory workaround, at least for my own theme settings of Simple/Mist.

I looked again in /usr/share/themes/Simple/gtk-2.0, found this section:

```
style "progressbar" = "default"
{
  fg[PRELIGHT] = "#ffffff"
}
```

and changed it to:

```
style "progressbar" = "default"
{
  fg[PRELIGHT] = "#ffffff"
  engine "redmond95" {  }
}
```

---

