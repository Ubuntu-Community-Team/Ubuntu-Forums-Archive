---
title: "My themes get Clearlookified!"
date: 2006-02-21
forum: Desktop Environments
---

### Post by SlugO on 2006-02-21
Okay, so I have this problem every time I try to use a theme that doesn't include Clearlooks. For some reason the outcome is totally different from what it's supposed to look like. It's like my themes are getting Clearlookified. Here's an example where the GTK theme **is the same** but looks totally different for me:

This is what Gentle theme should look like (includes GTK and Metacity):
[IMG]http://static.flickr.com/36/102743364_00463faa94.jpg[/IMG]

Here's what it looks like on my computer:
[IMG]http://static.flickr.com/28/102743363_22eb532219.jpg[/IMG]

Why is the GTK different? It's probably the thing causing also the different colors of the window borders. Seems like almost every time I use a non Clearlooks GTK I get this colored borders...

I installed some Clearlooks engine a few months back. Is that what's causing this? And do I need some other GTK engines cos I don't really know anything about them. Tips on changing the font used in windows would also be appreciated :)

Thanks.

---

### Post by SlugO on 2006-02-21
Anyone? This is quite an annoying problem, I thought that Gnome themes are supposed work without any special tricks unlike those of KDE's...

---

### Post by Wallakoala on 2006-02-21
The gtk theme changes the colors of the window borders. If you install the same gtk theme as the person in the screenshot has, and you use it, it should look just like the one in the screenshot.

---

### Post by SlugO on 2006-02-22
But it **is** the same GTK theme. :(

---

### Post by SlugO on 2006-02-27
So to repeat myself and summarize the whole problem:
Many of my GTK themes do not work the way they're meant to!

Am I really the only one with this problem? What have I done wrong then? :confused:

---

### Post by SlugO on 2006-09-03
Well, after over 6 months and 1 dist-upgrade to Dapper later I finally accidentally found out what the problem was.

I was poking around the ~/.gtkrc-2.0 for the first time actually and it looked like this:```
# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Clearlooks-DeepSky/gtk-2.0/gtkrc"

style "user-font"
{
	font_name="Sans Serif 10"
}
widget_class "*" style "user-font"

gtk-theme-name="Clearlooks-DeepSky"
gtk-font-name="Sans Serif 10"
```When I remove or comment out the include part I can finally get all my GTK themes working perfectly. Except for some Clearlooks_Cairo themes which seem a bit broken without that include.

You can bet that I won't be installing KDE alongside Ubuntu the next time I do a fresh install :-\"

---

### Post by Cuppa-Chino on 2007-03-07
hmm that does not work for me one bit

I have a custom theme and I cannot find it

I copied it to /usr/share/themes/  and all still no luck

---

