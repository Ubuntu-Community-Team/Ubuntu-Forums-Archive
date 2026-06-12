---
title: "File search menu item"
date: 2006-01-12
forum: Desktop Environments
---

### Post by fritz_monroe on 2006-01-12
I'm sure this is going to be a simple question, and I appologize for that.  I have been "customizing" my desktop and I've lost some menu items.  I used to have a menu entry that allowed me to search for files.  I installed a button bar and would like to include this file search as one of the button.  Could someone point me to this application?

I did a Google search for this, but searching for the term "search menu" makes it difficult to come up with what you need.  I just can't seem to get the search correct.

Any help is greatly appreciated.

F_M

---

### Post by Lambert on 2006-01-12
If you're talking about the search for files option under places it's called gnome-search-tool

---

### Post by fritz_monroe on 2006-01-13
That's exactly the thing I mean.  Is there a way to get that entire places menu back?  I created a new panel and when I moved it, the places menu disappeared.

F_M

---

### Post by Lambert on 2006-01-13
I'm not sure about getting the menu back but you can try this command from terminal

```
sudo dpkg-reconfigure -phigh gnome-panel
```

This will as it says reconfigure a package. It reads from the files it used when it setup the package so it may solve your problem or not. It may set the panel back to the default settings so any customization you've done may disappear.

---

### Post by fritz_monroe on 2006-01-13
I'll give that a shot.  As I'm new to Ubuntu and Gnome, I'm really just experimenting and I'm not overly happy with my setup just yet.  So starting over from scratch would work.  If nothing else, I found that I can put an entire menu onto a panel as a drawer, so I might be able to do it that way.

Thanks again.

F_M

---

