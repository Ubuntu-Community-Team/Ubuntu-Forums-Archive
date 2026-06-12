---
title: "Questions about Gnome."
date: 2007-11-24
forum: Desktop Environments
---

### Post by solarwind on 2007-11-24
Hey all, I'm testing out Gnome and have a few questions.

[COLOR="Silver"]1. How do I remove the minimize window animation?[/COLOR]
2. How do I set the title in a window title bar to be aligned left instead of centre?
3. The desktop icon grid in Gnome is not square-like as it is with KDE or windows. The horizontal grid is much closer together and it's hard to align the icons in a square grid.
[COLOR="Silver"]4. How do I disable showing window contents while dragging?
5. How do I disable showing window contents while resizing?[/COLOR]

---

### Post by rsambuca on 2007-11-24
I can tell already you won't like gnome. :)  If you want to do all that silly kind of tweaking, you may as well stick with kde.

I prefer Gnome, but the reality is that it isn't as configurable as kde, at least not as easily.

---

### Post by solarwind on 2007-11-24
> **rsambuca said:**
> I can tell already you won't like gnome. :)  If you want to do all that silly kind of tweaking, you may as well stick with kde.

I prefer Gnome, but the reality is that it isn't as configurable as kde, at least not as easily.

Lol, I remember being able to do all of this before, I just forgot how. It's been over 5 years since I used Gnome.

---

### Post by solarwind on 2007-11-24
Ok, the article below solved most of my problems, now only for problems 2 and 3.
[http://www.marksanborn.net/linux/turn-off-gnome-animations-and-hide-window-contents-while-dragging/](http://www.marksanborn.net/linux/turn-off-gnome-animations-and-hide-window-contents-while-dragging/)

Yay now my CPU doesn't spike to 95% when I drag a window!

---

### Post by rsambuca on 2007-11-24
Interesting.  I didn't think that that was possible.

---

### Post by solarwind on 2007-11-24
> **rsambuca said:**
> Interesting.  I didn't think that that was possible.
Anything is possible in Linux, you just need to know where to look ;)

The most annoying thing for me right now is the icon alignment which has a grid that is not a square.

---

### Post by mcduck on 2007-11-25
> **solarwind said:**
> Hey all, I'm testing out Gnome and have a few questions.

[COLOR="Silver"]1. How do I remove the minimize window animation?[/COLOR]
2. How do I set the title in a window title bar to be aligned left instead of centre?
3. The desktop icon grid in Gnome is not square-like as it is with KDE or windows. The horizontal grid is much closer together and it's hard to align the icons in a square grid.
[COLOR="Silver"]4. How do I disable showing window contents while dragging?
5. How do I disable showing window contents while resizing?[/COLOR]

2. If you are using Metacity, the default window manager, I don't thing there's a way to do this. With gconf-editor it's possible to change the order and placement of titlebar buttons, but there's nothing about the title itself. It could be possible by editing the metacity theme you are using but I don't think I've ever seen a metacity theme with title in any other place than center.

If you are using Compiz-Fusion instead, Emerald has easy way to change this. Just go to Emerald Theme Manager, and then Theme Settings/Edit Themes/Titlebar.  ON the right side there's a entry field where you can configure the titlebar layout, and also text explaining the different options. For a layout with menu button and title on left, empty on center and then minimize+maximize+close buttons on right the enrty  would be "IT::HNXC". 

3. Have you tried playing with the 'Compact Layout'-option in Nautilus settings?

---

### Post by Linteg on 2007-11-25
> **solarwind said:**
> 2. How do I set the title in a window title bar to be aligned left instead of centre?
Change the metacity theme, this is of course not really trivial but if you really want to, it is possible. Look at the attached diff (from a theme that has two versions, one with left-aligned text, and one with centered text) to see what kind of changes you have to make, it isn't much, but it can be hard to find the correct function to change...
> **solarwind said:**
> 3. The desktop icon grid in Gnome is not square-like as it is with KDE or windows. The horizontal grid is much closer together and it's hard to align the icons in a square grid.Nautilus doesn't really use a grid for the desktop, this is a dumb (my opinion) design decision, not sure if it's about to change anytime soon either, work on nautilus is sadly minimal (due to a lack of developers willing to work on it) although it is an important piece of the gnome desktop that many find lacking in some aspects.
However, there is work going on that could make this (a proper grid) possible, there's [this bug](http://bugzilla.gnome.org/show_bug.cgi?id=84390), which depends on another [pango feature](http://bugzilla.gnome.org/show_bug.cgi?id=327996), which, in turn a pango developer has [stated he plans to implement](http://bugzilla.gnome.org/show_bug.cgi?id=469313) in pango 2.20, which (probably) will be released about the same time as gnome 2.22.

---

### Post by solarwind on 2007-11-25
> **mcduck said:**
> 2. If you are using Metacity, the default window manager, I don't thing there's a way to do this. With gconf-editor it's possible to change the order and placement of titlebar buttons, but there's nothing about the title itself. It could be possible by editing the metacity theme you are using but I don't think I've ever seen a metacity theme with title in any other place than center.

If you are using Compiz-Fusion instead, Emerald has easy way to change this. Just go to Emerald Theme Manager, and then Theme Settings/Edit Themes/Titlebar.  ON the right side there's a entry field where you can configure the titlebar layout, and also text explaining the different options. For a layout with menu button and title on left, empty on center and then minimize+maximize+close buttons on right the enrty  would be "IT::HNXC". 

3. Have you tried playing with the 'Compact Layout'-option in Nautilus settings?

2. Thank you very much for this suggestion, I will surely try it out!
3. I did try it but I have no idea what it does.

Also, I don't use Compiz fusion or anything of that sort because my 6 year old graphics card has enough trouble just rendering my 1680 x 1050 resolution already.

> **Linteg said:**
> Change the metacity theme, this is of course not really trivial but if you really want to, it is possible. Look at the attached diff (from a theme that has two versions, one with left-aligned text, and one with centered text) to see what kind of changes you have to make, it isn't much, but it can be hard to find the correct function to change...
Nautilus doesn't really use a grid for the desktop, this is a dumb (my opinion) design decision, not sure if it's about to change anytime soon either, work on nautilus is sadly minimal (due to a lack of developers willing to work on it) although it is an important piece of the gnome desktop that many find lacking in some aspects.
However, there is work going on that could make this (a proper grid) possible, there's [this bug](http://bugzilla.gnome.org/show_bug.cgi?id=84390), which depends on another [pango feature](http://bugzilla.gnome.org/show_bug.cgi?id=327996), which, in turn a pango developer has [stated he plans to implement](http://bugzilla.gnome.org/show_bug.cgi?id=469313) in pango 2.20, which (probably) will be released about the same time as gnome 2.22.

Thanks so much for the reply. I'll try that now. I'm good in C/C++/Python/PHP/Java and all sorts of other languages, maybe I could have a go at the desktop grid thing. I'll post if I have any success.

---

