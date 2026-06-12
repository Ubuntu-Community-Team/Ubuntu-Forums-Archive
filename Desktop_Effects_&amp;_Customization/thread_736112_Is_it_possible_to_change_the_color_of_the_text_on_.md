---
title: "Is it possible to change the color of the text on the menubar?"
date: 2008-03-26
forum: Desktop Effects &amp; Customization
---

### Post by days_of_ruin on 2008-03-26
So that if you make it transparent and your background is dark you can make it white
so its still readable?

---

### Post by unoodles on 2008-03-26
Yes for some themes it is possible, just click system->preferences->appearence

then click on the customize button. then click on the Color tab

---

### Post by days_of_ruin on 2008-03-26
Can you name some themes that allow that?
I don't think I have any.

---

### Post by unoodles on 2008-03-26
the darklooks theme is a really good theme that allows it.

I would also recommend install the gnome-art package.
with this, you will be able to get the darklooks theme

---

### Post by threespacemen on 2008-03-28
> **days_of_ruin said:**
> So that if you make it transparent and your background is dark you can make it white
so its still readable?

You could also try using gnome colo(u)r chooser:

$ sudo apt-get install gnome-color-chooser

Once you've installed it, you can find it in the System menu. Click on the "panel" tab, select the radio button for 'normal' in the foreground column, then pick the colour that you want. Pretty straightforward. I'm no expert on gtk theming, but as this writes to the .gtkrc-2.0 file (sort of), it will override the colour of whatever theme you choose. I think... Still, easier than editing .gtkrc-2.0 or the theme by hand.

---

