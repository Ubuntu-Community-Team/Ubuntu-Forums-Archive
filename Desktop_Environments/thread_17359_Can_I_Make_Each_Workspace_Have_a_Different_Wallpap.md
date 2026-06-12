---
title: "Can I Make Each Workspace Have a Different Wallpaper"
date: 2005-02-28
forum: Desktop Environments
---

### Post by jerome bettis on 2005-02-28
as the title says, can I do that?  i know other window managers have this feature, what about gnome?   :-P

---

### Post by RichardA on 2005-02-28
I don't think Gnome can do this - not a technical limitation, but part of the work to simplify the interface.

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

### Post by agim on 2008-02-20
Great post. I really only use Compiz to show off when I am telling friends why they should switch. They are all cool people, the free as in freedom thing is right up their alley. They are also smart enough to get why viruses and spyware aren't an issue after a basic explanation. But its always the damn 3d desktop that does it :) This will make it look even cooler.
Thanks

---

### Post by xjgnsdof on 2008-02-20
I know what you mean. I'm going on one year with Ubuntu after starting with Feisty, and I try to bring people into the fold whenever I can. Hint: The best time to pitch Ubuntu is after they've just experienced a crash.

---

### Post by agim on 2008-02-21
lol, no kidding. Just after a crash or just after they first install Norton.
"Is the startup going to take this long... every time?"

---

### Post by katakaio on 2008-04-24
Excellent thread! The solution is elegant and works wonderfully. Could we mark this thread as solved? Maybe others who are wondering about this would check this thread out first.

---

### Post by nowhere@cox.net on 2008-05-11
I have noticed the compiz rendering of the wallpaper is not as high quality as the nautilus rendering. For example, the standard HARDY wallpaper has noticeable ring gradients in compiz but nautilus is very smooth. It looks like there are fewer colors in the palette for the compiz rendering of the background than for nautilus. 

Any ideas on this?

Thanks!

EDIT 1: I also noticed that the gradient rings appear when the panels are finally drawn after logging in. So I log in, there is a brief time when ONLY the wallpaper is visible and the quality is very high, with smooth transitions of colors. Once the top and bottom panels are drawn, the gradient rings suddenly appear.

EDIT 2: I turned the compiz splash on so I can see when it loads, and the order is this: login = high quality wallpaper, panels drawn = high quality, compiz starts = gradients appear.

---

### Post by Afromonkey0 on 2008-05-23
For making it look impressive, I'd recommend finding a massive panorama, or making one yourself (autostitch will run with WINE), cutting it up into 4 equal size bits with the GIMP and putting them in sequence as your backgrounds. I did this and it looks amazing. 360 degree panos are the best.

One complaint though, you lose your desktop icons, since they are part of nautilus.

---

### Post by Sneaky07 on 2008-05-23
I've followed this tutorial and it works very well but is there anyway to get shortcuts back on your desktop background or is that just me??

---

