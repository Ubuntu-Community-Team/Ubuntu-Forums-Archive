---
title: "fluxbox icons pixellated"
date: 2010-05-15
forum: Desktop Environments
---

### Post by thelatemail on 2010-05-15
Hi all,

I am currently running a Fluxbox system installed on top of a Karmic minimal install. I have just about everything I want up and running fine except for the icons in the iconbar/toolbar, which appear pixellated.

This doesn't seem to be the same issue others have had with the icons being discoloured/mangled as they display fine, but rather stretched to fill the toolbar. I thought this might be a technical limitation in Fluxbox, but the icons for folders when using Thunar render at a higher resolution (see attachment).

For the life of me I can't find where Fluxbox is sourcing the icon files from, or figure out what setting I would need to change to improve the rendering. Can anyone out there assist?

Thanks in advance.

---

### Post by entikryst on 2010-05-17
/usr/share/pixmaps/ is where the menu icons are stored.  The problem might be the size of the toolbar/iconbar which can be changes in the ~/.fluxbox/styles/(name of theme)/theme.cfg

---

### Post by thelatemail on 2010-05-17
Yep, the *menu* icons are, but these have an explicit icon set in the "menu" document so that is pretty easy to change. It however looks like a number of my iconbar icons are being sourced from my gnome icons theme directory at /usr/share/icons/gnome/16x16/apps

Now I just need to figure out how to get these to reference to a larger version of themselves in a sane way.

---

### Post by thelatemail on 2010-05-17
....and to update my own post, it appears the Firefox icon used in my iconbar/toolbar lives in the rather odd directory of /usr/lib/firefox-3.5.9/chrome/icons/default/default16.png

So my thinking is that icons are being dragged from all over the place in 16*16 pixel format and I can't for the life of me figure out any consistent logic to this. Is it because I am using a particular gtk theme that is somehow hinting these icons to Fluxbox? 

Short of going through and changing every 16*16 icon for each program using 'locate', what are my other options? I realise I'm probably trying to push a camel through the eye of a needle, but humour me here.

---

