---
title: "The really big cube"
date: 2009-02-08
forum: Desktop Environments
---

### Post by Go_Big_Blue on 2009-02-08
On Ubuntu's home site, if you click on the link "Take the Desktop Tour" (actual link is [http://www.ubuntu.com/products/whatisubuntu/810features/](http://www.ubuntu.com/products/whatisubuntu/810features/)) it will show a computer screen that flashes different desktop appearances, one of which is a giant cube.

I am trying to find how I can get the desktop cube to show up.  I have downloaded compiz, but can't seem to find how to make that specific cube pop up and stay popped up.  

Anyone have any experience with it?

---

### Post by overlord.gaurav on 2009-02-08
Once you have enabled the desktop cube. You can initiate it by pressing 'CTRL + ALT + Left mouse click'.
Now you get the cube formed.
Now you can release the CTRL and the Window Key, but you have to hold the left mouse to maintain the cube. And now you can spin the cube.

Hope the content is pretty clear.

---

### Post by steveneddy on 2009-02-08
> **overlord.gaurav said:**
> Once you have enabled the desktop cube. You can initiate it by pressing 'CTRL + Window key + Left mouse click'.
Now you get the cube formed.
Now you can release the CTRL and the Window Key, but you have to hold the left mouse to maintain the cube. And now you can spin the cube.

Hope the content is pretty clear.

On my compiz, this makes the water effect appear.

To rotate the cube, it's CTRL + ALT + Left Mouse Click

Hold down the mouse button and move it.

You'll get the general idea once you see it.

---

### Post by overlord.gaurav on 2009-02-08
Yeh, my bad! It was the incorrect combination.
The correct combination is, as mentioned by stevenedyy: "CTRL + ALT + Left mouse"

---

### Post by Go_Big_Blue on 2009-02-08
> **steveneddy said:**
> On my compiz, this makes the water effect appear.

To rotate the cube, it's CTRL + ALT + Left Mouse Click

Hold down the mouse button and move it.

You'll get the general idea once you see it.

Okay - I've done all that, but all I get is the panel of windows - I don't get the cube.  I have cube and rotate cube plugins installed, but still no luck, not even after rebooting.

---

### Post by pbotros1234 on 2009-02-08
Do the following in a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

Install it, and then afterwards open **System > Preferences > Advanced Desktop Effects**. You can adjust the shortcuts for all of your plugins and effects.

Oh and for the cube, make sure you have FOUR virtual desktops enabled (under General Options). And make sure **Desktop Cube** and **Rotate Cube** are enabled.

---

### Post by Go_Big_Blue on 2009-02-09
> **pbotros1234 said:**
> Do the following in a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

Install it, and then afterwards open **System > Preferences > Advanced Desktop Effects**. You can adjust the shortcuts for all of your plugins and effects.

Oh and for the cube, make sure you have FOUR virtual desktops enabled (under General Options). And make sure **Desktop Cube** and **Rotate Cube** are enabled.

Okay - still no luck.  Already had compizconfig-settings-manager loaded, as well as the plug-ins you mentioned.  

Again, I can rotate the workspaces using Ctrl+Alt+Left or Right Arrows, but when I hold down Ctrl+Alt+DownArrow, I don't see the cube. Instead, I see a panel of all 4 workspaces.

---

### Post by illurim on 2009-02-09
> **Go_Big_Blue said:**
> Okay - still no luck.  Already had compizconfig-settings-manager loaded, as well as the plug-ins you mentioned.  

Again, I can rotate the workspaces using Ctrl+Alt+Left or Right Arrows, but when I hold down Ctrl+Alt+DownArrow, I don't see the cube. Instead, I see a panel of all 4 workspaces.

Have you enabled 4 workspaces? If you only have 2 enabled, you won't see a cube. If you have your default gnome panel on the bottom showing your workspaces, right-click there and change it to 4.

EDIT: Woops, just re-read what you said. Duh me. Try going to an empty workspace and hold right-click on your mouse to move the cube - that's how I do it.

---

### Post by cptr13 on 2009-02-09
All this is done in the compiz config setting manager.
-Make sure you have 4 virtual desktops (though you can use the rotate cube effect with 2+ virtual desktops) by clicking "General Options" at the top.  Then Click the "desktop size" tab and set "horizontal virtual size" to 4.
-click back 
-in the "desktop" section, make sure the "desktop cube" has a check next to it and also the "rotate cube" box is checked as well.  If it mentions any conflicts go ahead and click through them, I always just disable whatever the conflicts are and that seems to work.
-If you want to change how you rotate the cube, click the "Rotate cube" icon (not the check box, but the icon itself) and click on "bindings" and then expand the "rotate cube" section.  I always like rotating with my middle mouse button alone, in that case you would the button on the right side of the "initiate" row and then change it to whatever you want.  For the middle mouse only you need to click "control" and "alt" (unhighlighting them), then hit the button1 dropdown and change that to button 2.  Then hit "ok" and then "back" to take you back to the main CCSM menu.

That is the basics of the rotating cube.  I'm guessing you don't have the right boxes checked or didn't resolve dependancies when it warns you.

Compiz is fairly complex...I've only scratched the surface of it so far but it's nice to look at.

Hope this solves the problem, please let us know...

---

