---
title: "Openbox Simple Theme"
date: 2008-06-03
forum: Desktop Environments
---

### Post by Koori23 on 2008-06-03
Okay, I just installed Openbox this morning. I've been playing with Window manager themes. I'm using Hardy, (whatever version of Openbox is in Hardy) and I'm having issues with "Simple". It's included by default. 

I have the padding how I want it. However, I can't get the text to center justify. 

I tried modifying in this way *menu.title.text.justify: center*

That didn't work. Here's the complete OBT.. If I can't get this to work, any other similar .obt's I can use that are flat black and center justified?

Here's the default obt file..

[I]# Name: Simple
# Author: Roberth Sjonøy <roberth.sjonoy@gmail.com>

# Menu settings
window.active.title.bg: raised splitvertical gradient
menu.title.bg.color: #000000
menu.title.text.color: #ffffff
menu.title.text.justify: center

menu.items.bg: Flat Solid
menu.items.bg.color: #000000
menu.items.text.color: #ffffff
menu.items.disabled.text.color: #ffffff

menu.items.active.bg: Flat Vertical
menu.items.active.bg.color: #ffffff
menu.items.active.text.color: #000000


# Window settings (focused)
window.active.title.bg: Raised Vertical
window.active.title.bg.color: #000000

window.active.label.bg: Parentrelative
window.active.label.text.color: #ffffff

window.active.handle.bg: Raised Vertical
window.active.handle.bg.color: #000000

window.active.grip.bg: Raised Vertical
window.active.grip.bg.color: #000000

window.active.button.unpressed.bg: Flat Vertical
window.active.button.unpressed.bg.color: #000000
window.active.button.unpressed.image.color: #ffffff

window.active.button.pressed.bg: Flat Vertical
window.active.button.pressed.bg.color: #000000
window.active.button.pressed.image.color: #ffffff

window.active.button.disabled.bg: Flat Vertical
window.active.button.disabled.bg.color: #000000
window.active.button.disabled.image.color: #ffffff

window.active.button.toggled.bg: Flat Vertical
window.active.button.toggled.bg.color: #000000
window.active.button.toggled.image.color: #ffffff


# Window settings (unfocused)
window.inactive.title.bg: Raised Vertical
window.inactive.title.bg.color: #000000

window.inactive.label.bg: Parentrelative
window.inactive.label.text.color: #ffffff

window.inactive.handle.bg: Raised Vertical
window.inactive.handle.bg.color: #000000

window.inactive.grip.bg: Raised Vertical
window.inactive.grip.bg.color: #000000

window.inactive.button.unpressed.bg: Flat Vertical
window.inactive.button.unpressed.bg.color: #000000
window.inactive.button.unpressed.image.color: #000000

window.inactive.button.pressed.bg: Flat Vertical
window.inactive.button.pressed.bg.color: #000000
window.inactive.button.pressed.image.color: #000000

window.inactive.button.disabled.bg: Flat Vertical
window.inactive.button.disabled.bg.color: #000000
window.inactive.button.disabled.image.color: #000000

window.inactive.button.toggled.bg: Flat Vertical
window.inactive.button.toggled.bg.color: #000000
window.inactive.button.toggled.image.color: #000000


### Everything else
border.width: 5
padding.width: 1
window.handle.width: 1
window.client.padding.width: 0
border.color: #000000
menu.overlap: 0
menu.title.text.justify: center

### Fonts
window.active.label.text.font:shadow=y:shadowtint=0:shadowoffset=0
window.inactive.label.text.font:shadow=y:shadowtint=0:shadowoffset=0
menu.items.font:
menu.title.text.font:shadow=y:shadowtint=0[/I]

---

### Post by Koori23 on 2008-06-03
GOT IT!!!

Sorry for the annoyance, It's my first time playing with these things.. It's

# Window title justification
window.label.text.justify: center

---

