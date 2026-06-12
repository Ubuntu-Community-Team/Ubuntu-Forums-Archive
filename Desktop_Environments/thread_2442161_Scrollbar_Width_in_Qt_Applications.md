---
title: "Scrollbar Width in Qt Applications"
date: 2020-04-30
forum: Desktop Environments
---

### Post by ChrisOfBristol on 2020-04-30
I'm on Ubuntu 20.04. I have made the scrollbar width for Gtk applications wider. It's much quicker to use since don't have to carefully align the pointer on a tiny scrollbar. I have plenty of screen width for the extra width of the scrollbar. (see how below)
This doesn't work for CherryTree which is a Qt application. (Or for LibreOffice, no surprise there then!) What do I need to do to get wider scrollbars on Qt applications? (And for LibreOffice, if that's possible.)

[HR][/HR][SIZE=2]For wider scrollbars on Gtk applications, create a file called ~/.config/gtk-3.0/gtk.css, containing 
```
scrollbar slider { /* size of the slider */ min-width:   20px; min-height: 20px; border-radius: 22px; /* padding around the   slider */ border: 5px solid transparent; }
```[/SIZE]

---

