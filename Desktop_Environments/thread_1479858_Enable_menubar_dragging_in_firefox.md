---
title: "Enable menubar dragging in firefox?"
date: 2010-05-11
forum: Desktop Environments
---

### Post by x-shaney-x on 2010-05-11
As you probably noticed, the "Light" themes (Ambiance and Radiance) as well as quite a few other gtk themes now enable moving windows by grabbing the menubar, which is quite useful with the unified titlebar/menubar style of certain themes.

So does anyone know of any way I can force Firefox to behave the same way.
I would prefer to do it through userChrome.css rather than adding an extension but whatever works.

Firefox is the only non-gtk app I use extensively so I'm not too bothered about any other apps that don't follow the behaviour.

---

### Post by lovinglinux on 2010-05-11
You can drag any window at any point, including outside the the window decoration, by holding ALT key.

---

### Post by x-shaney-x on 2010-05-11
But what if I'm eating an apple?  I don't have a spare hand to press a key and move the mouse at the same time :)

Nah, I really prefer just doing it the mouse only way.

---

### Post by lovinglinux on 2010-05-11
> **x-shaney-x said:**
> But what if I'm eating an apple?  I don't have a spare hand to press a key and move the mouse at the same time :)

Nah, I really prefer just doing it the mouse only way.

Hold the apple with your teeth :)

---

### Post by hariks0 on 2010-05-11
I don't think that the menu bar and Title bar are very far from each other. :) Anyway you can use Easystrokes to move any windows without any modifier keys. Install it from synaptic and enjoy.

---

### Post by lovinglinux on 2010-05-11
Same discussion [here](http://ubuntuforums.org/showthread.php?t=1480258).

> **hariks0 said:**
> I don't think that the menu bar and Title bar are very far from each other.

In fact, they are. Although Firefox uses GTK, the tool bars are XUL based, so I don't think they can interact the way other applications menu bars do. When you use ALT, the window manager probably "freeze" everything inside the window decoration and disregard the functions of inner interface, so it can move them altogether.

---

### Post by hariks0 on 2010-05-12
What about Easystroke anyway?

---

### Post by x-shaney-x on 2010-05-12
> **hariks0 said:**
> What about Easystroke anyway?

I think easystrokes is a bit much for what we are talking about.  I don't see it makes it any easier than moving those milimetres to the "proper" titlebar.

And if I keep grabbing the menubar because I forget it's not a proper gtk app I'm not likely to remember to use easystrokes.

Thanks for the pointer anyway though, I can find plenty of other uses for that :)

---

