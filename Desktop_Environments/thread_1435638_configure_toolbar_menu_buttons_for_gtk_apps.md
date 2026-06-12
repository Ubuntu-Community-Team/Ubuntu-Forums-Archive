---
title: "configure toolbar menu buttons for gtk apps"
date: 2010-03-21
forum: Desktop Environments
---

### Post by OliverN on 2010-03-21
I'm looking to edit the toolbar menu buttons for gtk apps.

It's this thing in Nautilus

[IMG]http://farm5.static.flickr.com/4003/4451711735_5cbbd500dc_o.png[/IMG]

Rhythmbox

[IMG]http://farm3.static.flickr.com/2724/4451711785_03fe457eea_o.png[/IMG]

And Evolution

[IMG]http://farm5.static.flickr.com/4025/4451711907_f18586d914_o.png[/IMG]

I'm not using the default theme but I'm sure it's recognizable. I remember it used to be done through 'Menus and toolbars' in Preferences/Menus and toolbars, but that seems to have disappeared in lucid. I've messed around with gconf-editor too, but I can't find the option. I'm running the beta 1 build. 

Knowledge?

---

### Post by asmoore82 on 2010-03-21
? To change the buttons style to the old one, you have open `gconf-editor`
and change the key "/desktop/gnome/interface/toolbar_style" to "both"

As far as changing what buttons are seen, I think this has to be done per application.

---

### Post by OliverN on 2010-03-22
The gconf setting was exactly what I was looking for, thanks. I hope the option to change it gets reimplemented in the standard interface.

---

