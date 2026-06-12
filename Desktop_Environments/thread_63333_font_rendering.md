---
title: "font rendering"
date: 2005-09-07
forum: Desktop Environments
---

### Post by eraclito on 2005-09-07
hallo,

I've got a problem with font menu rendering in some application like mplayer and audacity.

in the image my screen:

[IMG]http://www.netculture.it/schermata.png[/IMG] 

the other applications work well.

any idea on how to fixs it?

eraclito

---

### Post by Lux Perpetua on 2005-09-07
A non-GTK app like that won't render fonts like your usual programs. That said, your screenshot is really ugly. Can you choose a better font under the "Font" tab? Sorry, I'm not familiar with that application.

---

### Post by eraclito on 2005-09-08
[QUOTE=Lux Perpetua]A non-GTK app like that won't render fonts like your usual programs. That said, your screenshot is really ugly. Can you choose a better font under the "Font" tab? Sorry, I'm not familiar with that application.[/QUOTE]


font tab is for subtilte and cant fix my problem  :-?

---

### Post by skoal on 2005-09-08
Eraclito, check out this thread: [http://www.ubuntuforums.org/showthread.php?t=42317&highlight=mplayer+fonts](http://www.ubuntuforums.org/showthread.php?t=42317&highlight=mplayer+fonts)

* I know of no other alternatives (tools) than creating your own ~/.gtkrc file for older GTK-1.x apps, like mplayer.  If you discover some other means, then let me know.  I've tried installing GTK1 engines, but those don't help either.  Anyways, if you don't like the "helvetica" font (which requires you to install the msttf package), you can always fiddle around with different fonts using "xfontsel -print" from a terminal, substituting "helvetica" with what ever you choose.  That's old skool Xserver fossil font hacking.  I wish there were an mplayer GTK2 fork...

\\//_

---

