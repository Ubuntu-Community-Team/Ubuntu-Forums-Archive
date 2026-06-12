---
title: "How to set a mono-color environment"
date: 2011-09-23
forum: Desktop Environments
---

### Post by SharjeelHKh on 2011-09-23
Hi all, 
Can we set ubuntu environment to mono-color. 
I have seen that environment fades to gray scale during application unresponsive. I have seen a post on forum saying one can uncheck the fade effect during unresponsive. 
So there must be an option to set it by default also. 

Lets say if I want a mono color environment of [COLOR=DarkGreen][COLOR=DarkSlateGray]G[/COLOR][COLOR=DarkGreen]r[/COLOR][COLOR=SeaGreen]e[/COLOR][COLOR=SeaGreen]e[/COLOR][COLOR=Lime]n[/COLOR][/COLOR]-[COLOR=Black]S[COLOR=DimGray]c[/COLOR][COLOR=Gray]a[/COLOR][COLOR=Silver]le[/COLOR][/COLOR] instead of gray scale, What I would have to do???

---

### Post by mcduck on 2011-09-23
You could use the "Color Filter" plugin in Compiz to do that. Just enable it in CompizConfig Settings Manager.

The bad news is that it only has a *negative*-greenscale filter configured by default. You could try creating your own filter, based on the existing ones found in /usr/share/compiz/colorfilter/data/filters. Although the syntax definitely is a bit cryptic...

edit: It seems the plugin has no effect on Unity panels, though, and the effect only applies to windows open at the time you toggle it on. That's a bit of a pity, especially if you wanted the whole desktop and all programs to use the set color filtering by default. I'm quite sure this used to work better...

The Opacity, Brightness and Saturation-plugin works a bit better, you can set the saturation for all "any" to 0 to get a black&white display. Doesn't seem to affect Unity and  of only does black&white, so no green scale this way.

---

### Post by SharjeelHKh on 2011-09-26
ThanX mcduck, U solved my problem, I got what I was looking for. I am able to apply few of the available filters. Now I will tweak those filters for my desired opacity.

By the way I've done it to apply greenish FLIR system nightvision display for a simulator.

---

