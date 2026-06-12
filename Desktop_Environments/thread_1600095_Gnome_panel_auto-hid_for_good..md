---
title: "Gnome panel auto-hid for good."
date: 2010-10-18
forum: Desktop Environments
---

### Post by Stray Wolf on 2010-10-18
I put a gnome panel on the left of my desktop that displays a cpu monitor and a temperature monitor and set it to auto hide.  It auto-hid and hasn't came back.  I see the very edge of it on the left of my screen.  I'm using cairo-dock now and really don't need nor want the panel there.  How would I delete that panel without being able to show it or click on it?

---

### Post by kerry_s on 2010-10-18
use gconf-editor
go to: desktop-> gnome-> session-> required_components
remove: gnome-panel

---

### Post by Stray Wolf on 2010-11-10
Neato!  I found that keeping a gnome panel for a small notification area in a corner works well with cairo-dock.  That with compiz skydome enabled and my desktop snaps!

---

