---
title: "Icon Mixup in Theme Selector"
date: 2009-05-01
forum: Desktop Environments
---

### Post by floborg on 2009-05-01
I've just gone through two upgrades - from Hardy to Intrepid, and from Intrepid to Jaunty.  I was using the Hydroxygen icons in Hardy.  Now, the Appearance GUI shows the "unreadable" icon from Hydroxygen for most of the themes.

The screenshot shows what I mean.  The same X icon from Hydrogen is shown here even if I switch to Human or something else.

Any ideas on what happened?

---

### Post by 5nak3 on 2009-05-01
no idea what has happened, but have you rebooted the machine since the upgrades?

And also what happens if you remove the icon set in question and then reinstall it?

---

### Post by floborg on 2009-05-01
> **5nak3 said:**
> no idea what has happened, but have you rebooted the machine since the upgrades?

And also what happens if you remove the icon set in question and then reinstall it?

Thanks, but I beat you to it.  I've restarted multiple times, even with Human selected and Hydroxygen moved out of my home folder.  The problem persists.

---

### Post by floborg on 2009-05-02
Ok.  The icon type that appears in that particular spot is named either

image-missing
or
gtk-missing-image

This is understandable since that spot is used for application-specific icons.

That X is what hydroxygen uses for image-missing and gtk-missing-image.  It's also used for a number of other icon types like cancel, stop, close, unreadable, and nowrite.  I still see it when switching to another theme.  Root doesn't see it when I open the appearance dialog with gksu.  What's weird is that is also doesn't pick up my GTK theme or icon theme, even though I linked /root/.icons and /root/.themes to their counterparts in my home directory.  This trick works for nautilus and synaptic.

I've searched my system for extra image-missing or gtk-missing-image files that might have been strewn about during the upgrades, but nothing turned up.  I'm back where I started, although I uncovered a bug in this icon theme (where the X and the little lock icon were mixed up).

---

