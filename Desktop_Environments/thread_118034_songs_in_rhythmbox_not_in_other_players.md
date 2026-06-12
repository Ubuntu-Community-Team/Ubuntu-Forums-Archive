---
title: "songs in rhythmbox not in other players"
date: 2006-01-16
forum: Desktop Environments
---

### Post by potrick on 2006-01-16
Hey everyone. This is very odd to me, but when I'm in Rhythmbox my music collection is about 500 songs bigger than when I'm in any other player, including Amarok, bmpx, buine, Banshee, and others. I'm pretty sure this is because of m4a's and other iTunes filetypes, but why does Rhythmbox get to open them and nobody else?

---

### Post by bernardfrancois on 2006-01-20
[QUOTE=potrick]Hey everyone. This is very odd to me, but when I'm in Rhythmbox my music collection is about 500 songs bigger than when I'm in any other player, including Amarok, bmpx, buine, Banshee, and others. I'm pretty sure this is because of m4a's and other iTunes filetypes, but why does Rhythmbox get to open them and nobody else?[/QUOTE]

Rhythmbox tries to be more compatible with iTunes stuff I guess. But normally rhythmbox uses the gstreamer 'stuff' (dunno how they call it), which is a library (or similar) shared among multiple audio players. It's something typical from gnome, so other players like Amarok (which is more KDE-oriented) won't support it.
Any other player using gstreamer should normally play the same music. There are more, I dunno which. You could try searching synaptic for 'gstreamer' in name+description...

---

