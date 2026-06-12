---
title: "Compiz Fusion &amp; SuperKaramba Theme Drawing Problem"
date: 2009-06-22
forum: Desktop Environments
---

### Post by sokairyk on 2009-06-22
I run Ubuntu 9.04 64-bit with the latest updates and I use the Hardy 8.04 repositories only for the KDE applications since I don't want to install KDE4.

I have kdesktop running behind my gnome desktop so that I can use superkaramba without transparency problems.

When I switch to compiz-fusion I have a weird drawing problem with the superkaramba theme windows. They seem to draw an outline of each theme's window.

Here's what I mean:

Metacity Window Manager
[IMG]http://img146.imageshack.us/img146/4894/gnomesuperkaramba.jpg[/IMG]

Compiz Window Manager
[IMG]http://img29.imageshack.us/img29/1320/compizsuperkaramba.jpg[/IMG]


Now I know that not a real problem you don't notice it but if you have a lot themes and you use a more bright background it's not very nice.

Also the theme windows seem to break from the background on cube rotation...

I've played around with compiz window rules plug-in and I've removed the superkaramba class from every window animated event and 3D windows plug-in but I haven't seen any changes.

Any ideas?

---

### Post by sokairyk on 2009-08-09
While I was playing around with compiz-config options I found out that I just had to exclude the superkaramba window class from the shadow windows and decoration windows option under the Window Decoration plugin.

I just couldn't find it before cause I wasn't using emerald with compiz but the GTK Window Decorator.

---

