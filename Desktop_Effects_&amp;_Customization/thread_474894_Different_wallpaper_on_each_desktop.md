---
title: "Different wallpaper on each desktop?"
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by Error47 on 2007-06-15
Is it possible to have a different wallpaper on each side of the cube in beryl? It would really like it.

---

### Post by xjgnsdof on 2008-02-20
To have different wallpapers for each desktop, follow these steps:

**I. Disable "show desktop" in Nautilus**
1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

**II. Install Compiz Fusion**
1. In Terminal, input the following:
```
sudo aptitude install compizconfig-settings-manager
```
2. Exit Terminal

**III. Select your desktop wallpaper**
1. System --> Preferences --> Advanced Desktop Settings
2. Tick "Desktop Cube" and opt to disable desktop wall if prompted
3. Tick "Rotate Cube"
4. Select "Desktop Cube"
5. Click "Appearance" tab
6. Click "Add" under the "Background Images" field
7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear

---

### Post by darco on 2008-02-20
Thanks elgilicious...didnt think that was possible! Oh and I had to reboot to make it take effect.
thxs
darco

---

### Post by PaulFXH on 2008-02-21
@elgilicious
I didn't really think this was possible so easily. Thanks a lot.
However, I notice that the icons have dissappeared from my desktop even though Gconf>Apps>Nautilus>Desktop still has the same one checked to appear.
Any workaround for this?

Edit: OK, I see now that it's the Show Desktop uncheck step that did that.

---

### Post by darco on 2008-02-21
Well is there a workaround to add back my desktop icons? My screenlets survived but nothing else...
thxs
darco

---

### Post by PinkFloyd102489 on 2008-02-21
The only way I know of to fix this is to patch Nautilus. I tried to do it and it didnt work for me.

---

### Post by AndyNJ on 2008-02-22
i followed the steps above and have it all set up the way that I want, but how do i change the way the each image is displayed (e.g. stretch, fill, tile, etc)?

---

### Post by banelos on 2008-02-24
Sorry for reviving an old thread, but is it at all possible to have icons or stuff like Conky on your desktop while having a different wallpaper on each workspace?

If not it's really not worth doing this imo.

---

### Post by xjgnsdof on 2008-03-17
@ banelos and @ darco: I never have icons on my desktop, so I don't mind not having nautilus draw my desktop. Why have different desktops when you've cluttered them with icons? The main purpose of this effect is to associate certain desktops with certain tasks. Sorry, but I don't have a workaround yet.

@ AndyNJ: I would assume that you change that stuff in Compiz Fusion manager.

---

### Post by billybag on 2008-04-04
neat now how i undo this so i can have my icons. i tried selecting show desktop again. i tried unticking desktop cube... nothing... kind of miss my desktop icons being there along with conky

---

### Post by wesley_of_course on 2008-04-04
> **billybag said:**
> neat now how i undo this so i can have my icons. i tried selecting show desktop again. i tried unticking desktop cube... nothing... kind of miss my desktop icons being there along with conky

System - Preferences - gTweakUI - Nautilus    and put a check in the box next to, " use Nautilus to draw desktop"    and your icons should re-appear .

---

### Post by nuclearpidgeon on 2008-04-05
> **elgilicious said:**
> To have different wallpapers for each desktop, follow these steps:

**I. Disable "show desktop" in Nautilus**
1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

**II. Install Compiz Fusion**
1. In Terminal, input the following:
```
sudo aptitude install compizconfig-settings-manager
```
2. Exit Terminal

**III. Select your desktop wallpaper**
1. System --> Preferences --> Advanced Desktop Settings
2. Tick "Desktop Cube" and opt to disable desktop wall if prompted
3. Tick "Rotate Cube"
4. Select "Desktop Cube"
5. Click "Appearance" tab
6. Click "Add" under the "Background Images" field
7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear

note to anyone else who sees this, you should also make sure that the 'JPEG' plugin is enabled

---

### Post by Stason on 2008-04-05
Added 4 different wallpapers in Cube in Gutsy, JPEG is enabled. Does not work. All desktops show the wallpaper set in System==> Appeareance===>Background. What is wrong?

---

### Post by DXM31 on 2008-04-05
Now I have different desktops but snow and autumn leaves no longer work.
Is it because of the Icon thing?
Or
Something else?

---

### Post by nuclearpidgeon on 2008-04-05
> **Stason said:**
> Added 4 different wallpapers in Cube in Gutsy, JPEG is enabled. Does not work. All desktops show the wallpaper set in System==> Appeareance===>Background. What is wrong?

Make sure that the wallpapers are the same resolution as your monitor. I had to do this, I have a 1280x800 LCD laptop screen, and 3 of my images were 2560x1800 or something, can't remember. They were the same ratio (16:10), but they were too big, and as such, I was greeted by 3 blank desktops. make sure that they are EXACTLY the same (you can use the GIMP to do this)
You can also use this to emulate the 'Zoom' and 'Center' abilities of normal desktop images, by cropping the image, or adding a plain colour (or even a gradient) around the edge etc.

BTW does anyone know how to do this with Desktop Wall? And also,when I stopped Nautilus from drawing on the desktop, I logged in and rather than seeing a plain ubuntu colour while loading like normal, it showed my 1st background image. I was wondering if there's any way to make it still do this, so my background image shows up as soon as I log in, not after everything's loaded.

Also, do you think we should make a HOWTO for this? Because there are all these vital hints on the second page...

---

### Post by nuclearpidgeon on 2008-04-05
> **DXM31 said:**
> Now I have different desktops but snow and autumn leaves no longer work.
Is it because of the Icon thing?
Or
Something else?

It probably is from the icon change, perhaps those plugins rely on nautilus drawing the desktop.

---

### Post by MountainX on 2008-04-06
Is it possible to put a different screen saver on each desktop? I want to password protect one desktop. I thought an independent screen saver would be a good way to do that. I could work on other desktops, but when switching to that one I would just see screen saver or unlock prompt until entering password.

---

### Post by MountainX on 2008-04-06
For reference, here are some other threads on this subject:
[http://ubuntuforums.org/showthread.php?t=149130](http://ubuntuforums.org/showthread.php?t=149130)
[http://ubuntuforums.org/showthread.php?t=482505](http://ubuntuforums.org/showthread.php?t=482505)

---

### Post by Stason on 2008-04-07
> **nuclearpidgeon said:**
> Make sure that the wallpapers are the same resolution as your monitor. I had to do this, I have a 1280x800 LCD laptop screen, and 3 of my images were 2560x1800 or something, can't remember. They were the same ratio (16:10), but they were too big, and as such, I was greeted by 3 blank desktops. make sure that they are EXACTLY the same (you can use the GIMP to do this)

They are 1:1 pixel ratio. Still same one on all the desktops.:confused:

---

### Post by nuclearpidgeon on 2008-04-07
> **Stason said:**
> They are 1:1 pixel ratio. Still same one on all the desktops.:confused:

Are you sure you disabled nautilus? Also, if the background picture is a PNG or SVG, enable those plugins. If it's some other random format, or if all else fails, just convert it to JPEG.

---

