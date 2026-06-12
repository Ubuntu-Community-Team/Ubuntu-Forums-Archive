---
title: "Xfce desktop on 13.04"
date: 2013-06-08
forum: Desktop Environments
---

### Post by jamesd3rd on 2013-06-08
I've been trying a couple different desktops to see which one I like.  Unity I'm not a fan of and I like Gnome Fallback ok.  I decided to try Xfce but I don't have any icons when I use the file manager.  I just have text.  How do I get icons?

Thanks

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]jamesd3rd; Hi !...
I run XFCE4 on 13.04 as the platform....
Let's see; you have to have xorg for a GUI to run in 
```
dpkg -l xorg
```
then xfce4 must be installed ->status:
```
dpkg -l xfce4
```
and from the text login, to start the XFCE4 desk top:
```
startxfce4
``` pending creating and editing ~/.xinitrc
[/COLOR][INDENT=2][COLOR=#000000]
should workie great last long time ![/COLOR][/INDENT]

---

### Post by jamesd3rd on 2013-06-08
Odd, even though I did  few restarts nothing changed.  Just after I posted this, I did a restart and all my icons came back.  But is there a way to change the default icons?

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]jamesd3rd;

icons: yeah you can change them;
applications menu -> settings -> appearance -> icons 
If what is not available is unsatisfactory, others are available. See the xfce wiki for further details.
[/COLOR][INDENT=2][COLOR=#000000]
all's well that ends well[/COLOR][/INDENT]

---

