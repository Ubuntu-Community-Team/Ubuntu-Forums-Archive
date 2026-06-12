---
title: "kubuntu scaling on 4K screen"
date: 2020-10-19
forum: Desktop Environments
---

### Post by kruemelprinz on 2020-10-19
Hi
I have installed kubuntu 20.04 on my laptop with a 4K panel. Of course, as expected, the resolution made everything look very tiny at first, but i find the fractional scaling option set to 175% suits my needs best. I use Breeze-dark as my theme and I have set the GTK2 and GTK3 theme in system settings to the same.
However, there are some quirks related to desktop scaling that I wondered if anybody could help to resolve:

1) GTK3 apps like Evolution mail are partly unaffected by the scaling. Fonts scale correctly but the icons remain tiny. In some other GTK apps (like nautilus), even the window decorations are tiny despite the font size appearing correct. Also, other window items such as scrollbars are small and not as supposed.
This makes these apps practically unusable since I have to go so near the panel to see properly that my nose triggers the touch function ;)
Is there a way to apply correct scaling to all GTK items?

2) Mouse pointer size is inconsistent depending on its position. Over correctly scaled Qt apps, it's as intended, however against the desktop background, the pointer is tiny. Also, over incorrectly scaled GTK apps as in my first point, it is tiny. As soon as I hover over a desktop widget, again the size is correct. Funny enough, I set a KDE panel with startup menu, global menu, a blank spacer and a tray on one screen edge: The pointer changes size over every blank space in that panel.
Sometimes this weird behaviour makes me have to look really hard where the pointer actually is.

2) Context menus for KDE widgets are tiny as well. Again, fonts scale correctly, but the icons are super small.

I tried fiddling around in the system settings and increase the icons, but to no avail. Where they appear tiny, the size still remains unchanged.
Font sizes seem rather consistent I think because I set the "Force font DPI" option to a fixed value.

Is there any way to get a more consistent user experience by tweaking this somehow? (preferably by some easier way than messing around with the Breeze-Dark GTK theme CSS code, but I'll try if that's the only way...)

I'd really like to maintain the high resolution of the panel and not reduce to 1920x1080, since the whole user interface looks smoother (to me there is a noticable difference on a 15 inch panel between 4K and full HD).

All help is really appreciated,

---

