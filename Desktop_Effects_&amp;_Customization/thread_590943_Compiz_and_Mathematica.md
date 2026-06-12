---
title: "Compiz and Mathematica"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by geeree on 2007-10-25
I am using Mathematica 5.2 over our network through ssh on my laptop, which runs Ubuntu 7.10. I use Compiz for window management and find that Mathematica doesn't go well
with it. Mathematica notebooks are not rendered properly - text becomes unreadable and colours won't show. If I change the window manager to Metacity this problem goes away and Mathematica windows are rendered correctly. Is there any way I can correct this behaviour? Note that I had also faced this same problem on Ubuntu 7.04 with Beryl.

Girish.

---

### Post by mannheim on 2007-10-25
I think you can try (in a terminal) launching mathematica with:
```
export XLIB_SKIP_ARGB_VISUALS=1
mathematica
```

See [this post]("http://ubuntuforums.org/showpost.php?p=1549670&postcount=2") for example.

---

### Post by filterpipe on 2007-10-31
The quick workaround might be this:

Click on the "System" drop down menu in your system toolbar.
Select the Preferences nested drop down menu item.
Select the Appearance menu item.
Click on the "Visual Effects" tab.
Click on the "None" radio button.

Then play with Mathematica.

When you're done with Mathematica, you can go back and
set the "Visual Effects" to whatever you like.

Cheers....

---

### Post by geeree on 2007-11-01
> I think you can try (in a terminal) launching mathematica with:
```
export XLIB_SKIP_ARGB_VISUALS=1
mathematica

```


Thanks for the suggestion, mannheim, but that didn't work (I don't understand why). I finally resorted to deleting all my Screenlets and shutting down Compiz. Mathematica people say there's no "official" solution for the problem as yet. 

> The quick workaround might be this:

Click on the "System" drop down menu in your system toolbar.
Select the Preferences nested drop down menu item.
Select the Appearance menu item.
Click on the "Visual Effects" tab.
Click on the "None" radio button.

Then play with Mathematica.

filterpipe, isn't this is what called "shtting down Compiz"?! I wanted to avoid this because I happened to use half a dozen Screenlets on my widget layer and as soon as I shut Compiz down for using Mathematica, the widget layer vanishes and Screenlets fall down on the desktop with their ugly black boxes and cause a lot of trouble. Anyway, thanks for the suggestion though; this is exactly what I have been doing now-a-days. I deleted all the Screenlets.

Girish.

---

