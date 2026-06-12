---
title: "Is there a way to have transparent windows?"
date: 2011-02-04
forum: Desktop Environments
---

### Post by MR.UNOWEN on 2011-02-04
Hello,

Is there a way to have transparent windows, such that when I'm viewing a folder, that white background is see-through?

---

### Post by Copper Bezel on 2011-02-05
Short answer: no. Only the Terminal app really supports this.

Long answer: depends on what you want. Metacity has some selective transparency with the window frame, but not the area of the actual window itself; KDE takes this a bit further in recent versions, but it's still only the frame area that's transparent, like Windows 7. That said, you can set entire windows to whatever opacity you want through Compiz. Probably the most useful is the opacity setting in the Move Window plugin, which drops the opacity of a window to whatever setting you want while it's being moved - that helps quite a bit with a cluttered desktop, and it's easy to hit Alt+left click to check behind the focus window. If you're just going for flair, try the Opacity, Brightness, and Saturation plugin or the Trailfocus plugin. 

If you end up using Opacity, Brightness, and Saturation, one of the simplest things you can do is set a rule for type=menu | dropdownmenu | popupmenu | tooltip to opacity ~90%, which gives you transparent right-click menus, Gnome menu, etc. It's pretty and practical, because it means that when you right-click a piece of text or an item you're modifying in some way, that thing isn't entirely obscured. You might also decide to set opacities for specific apps, like name=nautilus | gedit | Gnome-panel | synaptic , which isn't necessarily practical but looks fairly cool. Notice that dark areas will seem more transparent than bright ones, though - if you have a light icon theme and a dark "input area" color in your Appearance settings, and Nautilus is set to 85% opacity, it'll look like you have opaque icons sitting on a transparent background.

---

### Post by Frogs Hair on 2011-02-05
I have not tried this and don't intend to . When the transparency option becomes an official part of a release I will check it out then. I have seen mixed reports on this PPA. [https://wiki.edubuntu.org/DesktopTeam/RgbaGtkWithPPA](https://wiki.edubuntu.org/DesktopTeam/RgbaGtkWithPPA)
[http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

---

### Post by Copper Bezel on 2011-02-05
I tried it a month back or so, and all it did was kill Nautilus until I removed it. (So literally nothing was drawing the desktop, meaning it was made entirely of artifacts of moved windows.) Yuck. Better to stick with the limited implementation in Compiz for now.

Because, I mean, transparent menus are still cool, right?  = )

---

