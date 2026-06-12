---
title: "GUI Launcher Icons - change, find, make your own..."
date: 2009-02-15
forum: General Help
---

### Post by 2CV67 on 2009-02-15
If you are seriously GUI like me, you probably have a lot of icons, particularly little icons around 5mm x 5mm on the top panel.

It can be a problem hitting the right one, especially if they are too similar (normal terminal & gksu-root-terminal for instance) or if they are identical (default application launchers if you don't specify anything special) or if they don't suggest the appropriate response to you (root-nautilus).

(Terminal Types are probably rolling in the aisles already - and this gets worse...)

If you want to improve the iconfusion situation, then:
- It's easy to change icons.
- There are a huge number of icons already in your Ubuntu to choose from without needing to look outside.
- It's quite easy to make your own.

For an icon on the panel:
1. How to change an icon.
- right click on the icon
- select 'Properties'
- in the 'Launcher Properties' window which opens, click on the picture of the icon.
- in the 'Browse icons' window which opens, scroll down to an icon you like, click on it & 'OK'.
- check that is OK on your panel or try again if necessary.

2. How to find an icon.
If you don't see anything you want in the 'Browse icon' window, you will need to browse to find something.
I have found this to be a laborious business, so if anybody knows a better way, please tell...
There are icons available at:
- /usr/share/pixmaps
- /usr/share/icons
You can look at them either in the 'Browse Icons' window or in Nautilus.
Using 'Browse Icons' you often get to what seem to be empty folders & you need to click on OK to open them & find they are not empty!
I find it more convenient & safer to do my browsing in Nautilus, then make the change in 'Browse Icons'.

You will find most icons are classed firstly by size (24x24 or 48x48 etc) which means you need to choose size first, then look for your icon.
This makes the whole thing long & painful!
I am not competent to recommend sizes, but I found 48x48 worked OK on my panel & I suppose 'Scalable' works anywhere (expert comments please?).

3. How to make your own icon.
If you don't see anything you like, or can't be bothered to look further, or want something special, then you can make your own.
I made some crude little ones using Gimp & may amuse myself by learning to do smarter ones some day.
- open Gimp.
- select File > New.
- set Width & Height to 48.
- paint your icon.
- save - I made a new Icon Folder in my home directory so I would not lose my icons during an upgrade (necessary??).
- go back to the bit about changing icons & navigate to your new icon.

Note that in Gimp you can generate text without needing to bitmap it yourself, then, if needed, shift the text layer to align with the rest.

Also note that you can open an existing icon in Gimp & modify it to suit yourself.
Remember to 'Save as' so you don't overwrite the original, and save it somewhere it won't be lost in an upgrade.

As an illustration here are, at 48x48:
- Regular Terminal
- Original Root Terminal (too much like Regular, especially at 5mm x 5mm)
- Root Terminal modified in Gimp
[ATTACH]103445[/ATTACH] [ATTACH]103446[/ATTACH] [ATTACH]103447[/ATTACH]

All the above was for icons on the panel.

I have no idea why, but icons on the desktop seem to behave differently!
For an icon on the desktop:
- right click on the icon
- select 'Properties'
- in the 'xxxx Properties' window which opens, click on the picture of the icon.
This opens a Nautilus window called 'Select Custom Icon'.
You can use that to navigate to /usr/share/pixmaps or /usr/share/icons or your own icons.
The presentation is inefficient though, with the icons often appearing as long lists & you need to select each one to see what it looks like in thumbnail on the right.
Maybe you can change this presentation, but I didn't find how.
Again, I think it is easier to find your icon in ordinary Nautilus, then navigate to it with the 'Select Custom Icon' screen.

Finally, for icons in the menus.
- right click on 'Applications'
- select 'Edit Menus'
- navigate to the icon you want to change
- select it
- Properties
- click on the picture of the icon
- this opens the 'Browse Icons' window just like on the panel
- follow the same procedure as for the panel.

I think that covers all the options, except looking outside Ubuntu for icons.
Please post your own suggestions for finding or making icons in this thread!
Particularly if you know how to browse all available icons easily...
Or if you know how to change the gray 'Shut Down' icon.

And please correct any errors in the above!

---

### Post by raequin on 2009-05-09
Hey, changing the icon for a (custom) launcher is not working for me.  What happens is that when I go to properties for the launcher and browse for an icon of my own, no files show up.  This is true even when I am in the directory containing the icons that come with Jaunty:

```
/usr/share/icons/hicolor/scalable/apps/
```

I would appreciate any help on this because I disna like the way that springboard looks, I wants my emacs icon.

As a related note, I installed emacs through terminal (aptitude get) but it does not show up on my Applications menu.  Know how to get this menu to update with new packages?

Thanks, yo.

Edit: Okay, I do not know how or why this worked, but I have my emacs icon on the custom launcher now.  What happened is that I accidentally put the path of the icon (.png) in the "command" box of the launcher's properties window.  The next time I used the launcher it said it could not execute the command "....png" or whatever.  I changed the command back to "emacs" and now the emacs icon I wanted to use is there in the panel.  WEIRD!

---

