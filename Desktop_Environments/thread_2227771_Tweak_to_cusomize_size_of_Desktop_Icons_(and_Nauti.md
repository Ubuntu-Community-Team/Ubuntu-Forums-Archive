---
title: "Tweak to cusomize size of Desktop Icons (and Nautilus Icons) in Trusty. Anyone?"
date: 2014-06-03
forum: Desktop Environments
---

### Post by FelixKay on 2014-06-03
Hey there,

im looking for a possibility to customize the general Desktop Icon Size with a pixel value.

As is commonly known u can adjust the size of the Desktop Icons (and Nautilus Icons) via the Nautilus Menue - EDIT - PREFERENCES - VIEWS - DEFAULT ICON ZOOM - to 30, 55, 66, 100, 150, 200 400 per cent. I'd like to have a size between 66% and 100% or, even better, in pts.

So.....where are these values stored?

Anyone?

Only thing I know is that you can reach the same Nautilus Preference via DCONF Editor (org - gnome - nautilus - icon view). As far as I can see it must be a Nautilus thing.

Any hints welcome.

Thank you guys



Felix

---

### Post by mc4man on 2014-06-03
Where nautilus settings are stored (~/.config/dconf/user), isn't relevant as there is nothing for you there.
The setting itself has 7 values available as a string ranging from smallest to largest vs. being set as an integer 

So if you wish to alter then get the nautilus source & have at it, maybe you can alter what the 7 strings produce or even  less likely switch to an integer setting
(or possibly find  nothing to be done easily.

---

