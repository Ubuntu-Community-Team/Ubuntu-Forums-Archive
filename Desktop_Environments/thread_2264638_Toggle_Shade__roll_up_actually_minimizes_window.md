---
title: "Toggle Shade / roll up actually minimizes window"
date: 2015-02-09
forum: Desktop Environments
---

### Post by ahobo on 2015-02-09
I'm trying to enable shade / roll up for windows in Ubuntu Gnome 14.10 on Gnome 3.14.
Instead of shading it minimizes the window... except without the minimize animation.

I've used Gnome-Tweak in Windows > Title Bar Actions > Double-click to Toggle Shade
I've also edited dconf: **org.gnome.desktop.wm.preferences.button-layout** to [B]:shade,minimize,maximize,close
[/B]
Clicking on the shade button also minimizes the window without the minimize animation. It just disappears.
(the minimize animation shrinks the window into the upper let corner)

I was hoping the shade / roll up would act like it does in XFCE where the titlebar remains and the window goes into the titlebar.


Sidenote: Does Compiz workin UbuntuGnome? I haven't got anything to work yet...

---

### Post by cmxilies2 on 2015-04-25
Well, Im in the same boat, though I've gotten my windows to shade by usings this > adrian@Dell:~$ gsettings set org.gnome.desktop.wm.preferences action-right-click-titlebar toggle-shade

I still miss the pleasant roll up action that compiz had.

---

