---
title: "Maximus in normal Gnome"
date: 2010-07-07
forum: Desktop Environments
---

### Post by Marceau on 2010-07-07
I would like to combine the best of the Ubuntu Netbook Edition and the normal Gnome of Ubuntu.

I'm on 10.04.

If at all possible, I'd like to see the following:

- either an adapted netbook interface without clutter but rather the normal Gnome application dropdown menus (I hate the extra click and context switch required to open a different application / directory in UNE now).

- or a normal Gnome interface with Maximus included. I really like the concept of Maximus and would like to use it in normal Gnome. I've tried starting it up in Gnome, but when I do, all windows lose their title bar and can't be moved/resized/closed anymore. This appears to be due to the fact that there's no set place for Maximus in the top panel in normal Ubuntu. Is there a way to change this? Also, if it is possible to change this, would the top panel still be able to autohide?

---

### Post by kerry_s on 2010-07-07
you can use maximus, it's just another program, i've used it in lxde, xfce4, jwm, etc...
use synaptic to install it
add it to your startup
go in to gconf-editor & uncheck the undecorate, so you keep the window buttons.

if you don't want the window decorations you need to install "window-picker-applet" & add it to the panel.

---

### Post by Marceau on 2010-07-07
> **kerry_s said:**
> you can use maximus, it's just another program, i've used it in lxde, xfce4, jwm, etc...
use synaptic to install it
add it to your startup
go in to gconf-editor & uncheck the undecorate, so you keep the window buttons.

if you don't want the window decorations you need to install "window-picker-applet" & add it to the panel.

Thanks for your swift reply. As I have the UNE installed, I already have both those items installed on my system.

It looks like the missing link for me is then how to add the title bar to the top menu bar (as is default on UNE). I thought Maximus was responsible for this. Perhaps I am mistaken.

I tried following your pointers and found that indeed adding window picker to the top panel did exactly what I wanted, without even the need to startup Maximus. Perfect! Thank you so much.

---

