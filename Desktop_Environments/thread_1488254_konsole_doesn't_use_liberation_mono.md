---
title: "konsole doesn't use liberation mono"
date: 2010-05-19
forum: Desktop Environments
---

### Post by mandar.mitra on 2010-05-19
I have set the konsole font to liberation mono, but I'm reasonably sure that the font that konsole is actually using is not liberation mono. It looks very different from the font used by xterm, emacs, gnome-terminal, etc.


Is there some font mapping hidden away somewhere that is overriding my choice?


Thanks,
Mandar.

---

### Post by portentum on 2010-05-20
Hmmm, I'm not seeing a difference here between konsole, evilvte and roxterm.

[[IMG]http://img98.imageshack.us/img98/4631/liberationmono.th.png[/IMG]](http://img98.imageshack.us/img98/4631/liberationmono.png)


~/.kde/share/apps/konsole/Shell.profile has the correct font set?

---

### Post by mandar.mitra on 2010-05-20
Here's the appearance section from that file:


[Appearance]

AntiAliasFonts=true
ColorScheme=Linux
Font=Liberation Mono,12,-1,5,50,0,0,0,0,0

Yes, my fonts look kind of like yours, but they look different (thicker) in xterm / emacs, and I prefer that appearance. Here's a screenshot.

---

### Post by portentum on 2010-05-20
To me it looks almost like the difference between Regular and Bold.

[[IMG]http://img28.imageshack.us/img28/8178/libmonoregularvsbold.th.png[/IMG]](http://img28.imageshack.us/img28/8178/libmonoregularvsbold.png)

[SIZE="1"](sorry about the imageshack links, I did not want to resize the image and make the fonts suffer because of it, and the forums do not allow attachments of that size)[/SIZE]

---

### Post by Zorael on 2010-05-20
This may be that Konsole listens to KDE's font hinting settings, whereas non-KDE apps listen to GNOME's setting and/or fontconfig (as defined in your **~/.fonts.conf** and **/etc/font/conf.d/** files).

Could it be that you have KDE set up to render fonts with full hinting, and GNOME/fontconfig up to use ~medium hinting? GNOME uses weird names for this, like "Best shapes" and "Monochrome" and whatnot. I'm not sure how they translate to hintnone, hintslight, hindmedium and hintfull, though.

That said, I think Konsole overrides all settings a bit since it offers its own option for toggling antialiasing. I'm not sure to what extent, though.

---

### Post by mandar.mitra on 2010-05-22
I've managed to fix the problem. Just recording what happened in case it's ever useful to anyone.


It turns out if I explicitly do "xrdb < .Xresources", this messes things up - konsole's fonts look like they do in the screenshots, and the fonts for gnome-based applications (e.g. gnome-panel, and synaptic) also look thin and under-fed.*


If I don't run xrdb as above, my .Xresources are still automagically sourced, but the original problem disappears. Konsole fonts, as well as fonts on gnome applications look the way they are supposed to.


Can't explain the fix, but I'm glad the problem's solved.*

---

