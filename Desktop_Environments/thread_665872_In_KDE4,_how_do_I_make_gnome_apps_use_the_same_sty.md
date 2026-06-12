---
title: "In KDE4, how do I make gnome apps use the same style?"
date: 2008-01-12
forum: Desktop Environments
---

### Post by Sarke on 2008-01-12
What the title says.

I tried installing qtcurve and such, but nothing changed and no settings showed up.  Any ideas?

---

### Post by emerson999 on 2008-01-12
The only thing that's worked for me is to manually load up the gnome control center(search gnome configuration in the kde4 menu), and select appearance. On doing so, it'll instantly change the style on loaded gnome applications.

---

### Post by Sarke on 2008-01-14
Thanks, worked for me too, but it only made the GNOME apps look like the GNOME theme.  I want them to look like the KDE theme.

---

### Post by smartboyathome on 2008-01-15
As of right now, you can't. QTCurve is only available for KDE3.

---

### Post by dancantong on 2008-01-15
> **emerson999 said:**
> The only thing that's worked for me is to manually load up the gnome control center(search gnome configuration in the kde4 menu), and select appearance. On doing so, it'll instantly change the style on loaded gnome applications.

Yes, it works but when I close the session and start again I have to load again the gnome control center.
Is there any way to avoid doing it and see gnome applications (like Firefox) without so ugly look?

---

### Post by Rumo on 2008-01-15
> **Sarke said:**
>  Any ideas?

If you seriously consider switching to KDE I would recommed that you switch to KDE programs, too. Sure, not yet all programs were ported to KDE 4.0 but the KDE 3 programs are great, too. The applications are the main reason why I went for KDE in the first place!

amarok, digikam, konqueror, dolphin, konsole+yakuake, kontact, gwenview, okular, kate, kile, kopete, dragonplayer are just some examples...

---

### Post by TeaSwigger on 2008-01-15
Understand I don't use KDE4 at this time, so I'm only offering ideas. But on the topic of allowing to change Gnome (GTK) apps without running the Gnome services, wouldn't it be possible to use the GTK2x theme switcher, gtk-chtheme, to chose a style for Gnome apps? 

Granted that sets the style but not color, which would be goverened by the particular GTK theme. Here in Kubuntu Gutsy, I've noticed that a couple of GTK themes have been modified to read the Qt (KDE) colors. Geramik is one, forget the others atm. This is distinct from the QtCurve type of management. I don't know how this was done, but it seems others could also be so modified.

---

### Post by Lord Blackadder on 2008-01-15
This is how I managed to get Firefox to use the Qt theme:

I noticed that I had a file in my home directory called .gtkrc-2.0 that contained this info:

[FONT="Courier New"
]# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

style "user-font"
{# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

style "user-font"
{
	font_name="Arial 8"
}
widget_class "*" style "user-font"

gtk-theme-name="Qt"
gtk-font-name="Arial 8"

	font_name="Arial 8"
}
widget_class "*" style "user-font"

gtk-theme-name="Qt"
gtk-font-name="Arial 8"
[/FONT]

I had also noticed files in ~/.kde4/share/config called gtkrc-2.0.  I backed this file up, copied the .gtkrc-2.0 from my home directory and renamed it, removing the leading period.  After this, Firefox loaded up using the Qt theme instead of that ugly ugly default GTK theme.  Also, I found that by simply changing the Qt part to QtCurve, you could use the QtCurve theme instead.

I have noticed that every so often this file gets overwritten.  I've tried making it read-only but so far that hasn't worked.  That GTK theme is so ugly though that I feel compelled to change it back every time.

But this work-around seems to do the trick for me.

---

### Post by timseal on 2008-01-23
Thanks, two small points: it was copying ~/.gtkrc2.0-kde to ~/.kde4/share/config/gtkrc-2.0 that did the trick; and I think your gtkrc-2.0 file should actually stop at the first gtk-font-name="Arial 8".

A further discovery - the fonts in the apps themselves hadn't changed.  I ran gconf-editor, and changed the /desktop/gnome/font-rendering key (in my case to slight, but I suspect it will work for any option).  This made the fonts look better instantly.

---

### Post by maestrobwh1 on 2008-05-17
Finally a solution:-)

I merely copied the portion of the gtkrc-2.0 into my own /.kde4/config/gtkrc-2.0 (after opening it and deleting its contents) so it looks like this (and made permissions read only, even for myself):

# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

style "user-font"
{# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

style "user-font"
{
font_name="Arial 8"
}
widget_class "*" style "user-font"

gtk-theme-name="Qt"

---

