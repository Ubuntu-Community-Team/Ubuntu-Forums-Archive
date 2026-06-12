---
title: "How can I disable the focus rectangle in Gnome?"
date: 2008-10-08
forum: Desktop Environments
---

### Post by onezero on 2008-10-08
Hello there!

I've recently been noticing the unsightly dotted focus rectangle through the Gnome GUI and was wondering if there is a way to disable it?  Any help is much appreciated, thanks in advance!

---

### Post by tuxxy on 2008-10-08
Do you mean the compiz magnify tool?

If you do simply disable it in your ccsm at accessibility > magnifier

---

### Post by onezero on 2008-10-08
Hi, thanks for your response.

No, not the magnifier tool.  The focus rectangle is a dotted rectangle that surrounds whatever window element that currently has the focus for input.

For instance, if you open a window that has tabs, and select the second tab, you should then see a dotted rectangle around the title of it showing that it currently has the focus.

Edit: I am in the process of uploading a screenshot to show what I mean. :)

---

### Post by onezero on 2008-10-08
[IMG]http://www.yourfirefly.com/images/screenshot.jpg[/IMG]

---

### Post by onezero on 2008-10-08
Bump.

---

### Post by onezero on 2008-10-08
Anyone?  I'm assuming its a simple edit of a style file somewhere, but I'm not sure at all where the gnome theme files are located, or what I'd have to change.

---

### Post by jamarks1 on 2010-01-03
I would also like to know this as well, not to make the focus rectangle go away however; but to make it bigger! I don't like using the mouse and sometimes get lost in Tab Hell trying to look for the 1 pixel dotted focus rectangle. Let's make it 3 pixels and yellow or something. Let's make a small pulsation animation to go along with a change in focus so you can actually see the damn thing.

I've gotten as far as finding the references which denotes the focus rectangle's style. It's **focus-line-width, focus-line-pattern, and focus-padding** in [this]("http://library.gnome.org/devel/gtk/unstable/GtkWidget.html")GtkWidget document. I'm not a programmer so I have no idea which file needs to be changed. 

Sorry for resurrecting an old thread.

---

