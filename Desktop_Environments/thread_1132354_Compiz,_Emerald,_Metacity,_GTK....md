---
title: "Compiz, Emerald, Metacity, GTK..."
date: 2009-04-21
forum: Desktop Environments
---

### Post by Volt9000 on 2009-04-21
I'm still trying to get the hang of themes but not having much success.

Particularily I'm having difficulty understanding the difference between all those items in the title: Compiz, Emerald, Metacity, GTK, and I'm sure there are others that I can't remember at the moment.

Are all of these just windows managers, i.e. they all handle graphical rendering? Or are there specific ones that handle rendering of specific components? I downloaded a theme recently and all it seemed to do was change the look of the titlebar and min/max icons. The widgets didn't change.

If I make a theme, will that theme work with any manager, or only specific ones?

And finally, is there a good tutorial somewhere on making my own theme?

[Edit]
Ok it seems that metacity is JUST for window border decoration, i.e. the titlebar, text within it, and buttons. What if I want to change the look of widgets as well?

---

### Post by Volt9000 on 2009-04-22
*bump*

Any takers?

---

### Post by rainwalker on 2009-04-22
Your confusion is TOTALLY understandable :)

Compiz - This is a nifty little bit of software that provides all fo the eyecandy and effects for the desktop. It's what's called a "compositing window manager", for reasons too technical to be relevant to an average user. You can enable it under the "Visual Effects" tab under System > Preferences > Appearance. As PacSci stated later on in this thread, Metacity and Compiz are both compositing window managers (handling the placement of windows) and both have built-in decorators, but Metacity is the GNOME default while Compiz must be installed seperately (but included in Ubuntu for the past few releases).

Emerald - A window decorator that must be used with a compositor (like Compiz). It handles the window borders and shadows, and is a lot more customizable than the default Metacity window decorator. However, as far as I know, there isn't much development going on with it, but many people are happy with it in its current state. The themes for it are usually a lot fancier than Metacity ones and can be customized personally, but they don't match your color scheme/theme automatically like Metacity tries to do. Check it out, you can always uninstall it if you don't like it

Metacity - The default window decorator for Gnome and Ubuntu, it's what handles the window borders and shadows.

GTK - This is what creates the general user interface (the buttons and widgets and stuff). Take a look at Kubuntu, which uses Qt instead of GTK, and you'll see how the overall appearance differs. 

Gnome-look.org is a fantastic place to get GTK, Metacity, Emerald, GDM (login screen), and icon themes :)

---

### Post by Volt9000 on 2009-04-23
Ah I see, ok that clears things up a bit, thanks.

As far as customizing the theme goes, how do I do this? It seems that Metacity (and Emerald?) is only for borders. What if I wanted to change the look of widgets and whatnot?

---

### Post by rainwalker on 2009-04-23
That is what GTK themes are for (they will sometimes include an icon set and/or window border as well)

---

### Post by Volt9000 on 2009-04-28
And how do I built my own themes? I've been looking for a comprehensive guide on this, but none seem to exist. The information is scattered all over the place...

---

### Post by coffeecat on 2009-04-28
> **Volt9000 said:**
> And how do I built my own themes?

Have a look on [http://art.gnome.org/](http://art.gnome.org/) . There are links to some tutorials in the bottom right of that page.

Also have a look at the themes there. They're older and only include Gtk and metacity, but are much better put together because (I think) they've all been vetted before being put up - except with the proviso in my edit. There's some good ideas on gnome-look, but I find it disappointing. Many of their themes are sloppily put together.

**Edit:** Should have added - I'm finding some of the Gtk and icon themes from art.gnome don't install properly in Jaunty, where they worked fine with previous releases and other earlier distros. An example is the Yasis icon theme. In Jaunty, the Yasis folder design doesn't show up, the default gnome one appearing instead. I think the latest version of gnome has introduced some incompatibilites, which is a pity.

---

### Post by PacSci on 2009-04-28
Actually, it's a bit different than what rainwalker described.

Metacity and Compiz are BOTH compositing window managers - they handle the placement of windows onscreen. They also both have built-in decorators. Metacity is the GNOME default, but Compiz must be installed seperately. To paraphrase Havoc Pennington (Metacity's creator), Metacity is like Cheerios, but Compiz is like marshmallow Froot Loops.

Emerald is a decorator like rainwalker said. Compiz and Metacity each have their own window decorators, but Compiz's can be swapped out with Emerald. Emerald themes don't match the GTK theme.

GTK is the widget set - it draws the dialog boxes, buttons, text boxes, and the like. The reason GNOME and KDE apps look different is because they used different widget sets - GNOME uses GTK, and KDE uses Qt. Generally, when people talk about themes, they refer to GTK themes. GTK themes can define window borders, but only the default Compiz and Metacity decorators use them.

I hope this explains things instead of confusing you even more.

---

### Post by rainwalker on 2009-04-28
> **PacSci said:**
> Actually, it's a bit different than what rainwalker described.

Metacity and Compiz are BOTH compositing window managers - they handle the placement of windows onscreen. They also both have built-in decorators. Metacity is the GNOME default, but Compiz must be installed seperately. To paraphrase Havoc Pennington (Metacity's creator), Metacity is like Cheerios, but Compiz is like marshmallow Froot Loops.

Emerald is a decorator like rainwalker said. Compiz and Metacity each have their own window decorators, but Compiz's can be swapped out with Emerald. Emerald themes don't match the GTK theme.

GTK is the widget set - it draws the dialog boxes, buttons, text boxes, and the like. The reason GNOME and KDE apps look different is because they used different widget sets - GNOME uses GTK, and KDE uses Qt. Generally, when people talk about themes, they refer to GTK themes. GTK themes can define window borders, but only the default Compiz and Metacity decorators use them.

I hope this explains things instead of confusing you even more.

Ah, thank you for correcting me :)

---

### Post by SirGe on 2009-10-28
This should be REQUIRED reading before trying to touch a Gnome desktop :)

Thank you for the enlightenment!

---

