---
title: "Emblem position with Tango, Human, Crux..."
date: 2005-10-18
forum: Desktop Environments
---

### Post by bdash on 2005-10-18
I am using the Tango icon theme, and I noticed a strange bug. It is the same problem with the Human icon theme and the Crux theme.

Instead of appearing on the icon, Nautilus' emblems appear on the top left of it. This is ugly, takes space...

I had a look instead of the theme to find how to correct that, but I didn't find any reference to the emblems position. Also a Google search does not return anything about emblems positionning.

Any idea to put the emblems at the right place?

---

### Post by felipe on 2005-10-18
that's the way they are intended to work AFAIK.

the reason is you can add two or more emblems to an icon, each appearing in his own space, ie not overlapping, in order to stay visible

---

### Post by bdash on 2005-10-18
Ok, when I try the Gnome icon set I have a small overlap on an icon with 3 emblems. I can accept that the position in the Tango icon set is a feature rather than a bug.

Now, how can I modify the Tango icon set to behave like the Gnome icon set with respect to the emblems?

---

### Post by HanZo on 2005-11-17
> Instead of appearing on the icon, Nautilus' emblems appear on the top left of it. This is ugly, takes space...

I perfectly agree on this point, and I would be very interested to know how to mod the theme to make the emblem position fit on the icon like in the default gnome theme!

---

### Post by varunus on 2005-11-17
This is a theme specific detail, I know that much...but I don't know how to do it.  You could check in the index.theme file for the iconset and see if you see anything.

Also, you might want to email one of the icon theme authors on Gnome-look ([www.gnome-look.org)](www.gnome-look.org)), I'm sure they'd know.

But its not a bug.  :)  I like the way the gperfection2 and graphite themes handle where they put their emblems, personally...

---

### Post by HanZo on 2005-11-17
>  I like the way the gperfection2 and graphite themes handle where they put their emblems, personally...
that's exactly the style I'd like it to have!

anyway the guys on art.gnome.org say:
>  HanZo: the emblem uncontrolled size behavior is current an issue to be fixed soon in next Nautilus version. You don't have to mod anything
so... we'll just have to wait and hope it gets fixed soon...

---

### Post by secstate on 2006-01-02
This is a bit of an old thread, but I went poking around in the Tango Unofficial (from art.gnome.org) index.theme file and discovered that changing the size= number at the bottom of the file for emblems to 64 auto-scaled the emblems to a much more palatable size.  You can also just type in whatever number strikes your fancy there and see how it looks by saving the file.

---

