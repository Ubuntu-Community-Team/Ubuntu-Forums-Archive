---
title: "How can I remove all button icons?"
date: 2007-04-09
forum: Desktop Environments
---

### Post by rio_hot on 2007-04-09
Hi all,
It seams that every button in almost every app has an icon next to it.
These icons detract from the app and clutter the UI.
I have found options to change everything accept removing the redundant icons.
Please, does anyone know how they can be removed?
Many Thanks

---

### Post by kerry_s on 2007-04-09
What apps?

Maybe you should change your environment to something thats more in line with your needs. Like a different WM(window manager). There are several that are scarce right out of the box. I use fluxbox and various light app's.

---

### Post by ComplexNumber on 2007-04-09
> **rio_hot said:**
> Hi all,
It seams that every button in almost every app has an icon next to it.
These icons detract from the app and clutter the UI.
I have found options to change everything accept removing the redundant icons.
Please, does anyone know how they can be removed?
Many Thanks
which buttons are you referring to? those on the toolbar or those on actual buttons? its possible to remove icons from toolbars so that it looks like in the screenshot for nautilus (screenshot 1 = without icons).

to remove the icons from the toolbar, fire up gconf-editor, go to Edit in the menu, then Find. type in "icon" and tick the 2 tickboxes. scroll down to /desktop/gnome/interface/menus_have_icons. type in "text"

---

### Post by mcduck on 2007-04-10
> **rio_hot said:**
> Hi all,
It seams that every button in almost every app has an icon next to it.
These icons detract from the app and clutter the UI.
I have found options to change everything accept removing the redundant icons.
Please, does anyone know how they can be removed?
Many Thanks

System/Preferences/Menus & Toolbars and change "Toolbar button labels" to "Text Only" and unselect "Show Icons in Menus". That should remove major part of icons from your apps, but some programs may have settings of their own for this kind of things (Firefox, Synaptic and  OpenOffice at least).

---

### Post by rio_hot on 2007-04-10
Hi,

Thanks for the reply.
The icons I wish to remove are the icons from actual buttons.
I don't need:
        a "tick" next to the word "OK" on dialogue boxes;
        a "diskette" next to the word "Save" or "Load";
        a "swerl" next to the word "refresh".

These icons are surplus and make to product look..... well cheap!
Also I really like the rest of gnome and the WM (Beryl), is just the icons are driving me nuts. (really is because they make everything so chunky).

Thanks again for any help.

---

### Post by ComplexNumber on 2007-04-10
> **mcduck said:**
> System/Preferences/Menus & Toolbars and change "Toolbar button labels" to "Text Only" and unselect "Show Icons in Menus". That should remove major part of icons from your apps, but some programs may have settings of their own for this kind of things (Firefox, Synaptic and  OpenOffice at least).
oh yeah....you're right....only just noticed that  :D. that used to be part of a separate package called gtweakUI, but i guess  it must have been introduced into core-gnome sometime. i remember that it had 4 mini packages that were used for further customising nautilus,epiphany, menus and splash screen.



> **rio_hot said:**
> Hi,

Thanks for the reply.
The icons I wish to remove are the icons from actual buttons.
I don't need:
        a "tick" next to the word "OK" on dialogue boxes;
        a "diskette" next to the word "Save" or "Load";
        a "swerl" next to the word "refresh".

These icons are surplus and make to product look..... well cheap!
Also I really like the rest of gnome and the WM (Beryl), is just the icons are driving me nuts. (really is because they make everything so chunky).

Thanks again for any help.
i suppose you could design your own icon theme that uses 100% transparent icons. what you would need to do is to change the stock icons to be invisible(ie transparent, in this case), then tell the icon theme to inherit abother theme. all you would need to do is (say) take any icon theme, make the stock icons transparent, then make that theme inherit the theme that it comes from. you woud have to delete the stock icons folder from the theme that it inherits, though.
hope i've explained that clearly enough.

---

### Post by juaka on 2008-01-06
He is refering to the stock icons on the buttons. For example | X Cancel |

To disable those icons:
1. Open the gtkrc of your theme.
If your theme is Human, ```
sudo gedit /usr/share/themes/Human/gtk-2.0/gtkrc
```2. Copy and paste this option at the top of the document.

```
   gtk-button-images = 0
```3. Refresh your theme, so it recognize the changes. For that open the theme selector, select another theme and select the previous theme.

---

