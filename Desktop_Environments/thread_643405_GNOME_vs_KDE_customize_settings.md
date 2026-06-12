---
title: "GNOME vs KDE customize settings"
date: 2007-12-17
forum: Desktop Environments
---

### Post by ulisesrangel on 2007-12-17
I have used kde and gnome by fedora, pclinuxos, freespire, mint, etc.
I decided stick with ubuntu, but cant decide kde or gnome, i try one for a few weeks and then switch to the other, i have switched many times, so i ask for help to customize either to my needs.
I will put what i like and what i need to change, but dont know how, if you know how thx in advise.

GNOME really want , kde have
1.panels completely auto hides leaving full screen to windows (in gnome remain part of the panel)
2.cd appending (like in k3b, you can add files to a cd already with files)

KDE really want, gnome have
1.dolphin open with double click (its really annoying when you try to select a file for rename, copy, view information,etc and you ended up running or opening the file)
2.files permission when copying from a cd (i backup to cd, and when restore this directories and files always get copied only with read permission even for the owner, that dont work for me since this files need to be updated frequently)
3.better integration with compiz fusion

I havent tried Xubuntu, i will, maybe it work better for me.

Also if anyone know how to save the panels settings, i customize the panels a lot, but dont know how to save the configuration, so after a fresh install i have to customize the panels again.

thx

---

### Post by tgilber1 on 2007-12-17
1.  To hide panels in gnome, right-click on panel and select auto-hide
2.  To get k3b like features with Gnome, try GnomeBaker
3.  To save your panel between installs or updates, copy recursively the following directory .gconf/

ex. cp -R /gconf/ gconf.bak

---

### Post by Landrovan on 2007-12-17
In KDE (Kubuntu) to select a file on a single click, and open on double click, it's an option.

Go System Settings -> Keybord and mouse -> Mouse
And select double click to open

---

### Post by SparklingWater on 2007-12-17
Unfortunately, GNOME does not fully auto hide the bars. It still shows like 3 pixels.

---

### Post by ulisesrangel on 2007-12-19
Thx all for you tips...

I try xubuntu, i really like the fast and easy configuration (all from one link), but the "update-framerst -u -k  `uname`" or something cant fix my long black screen boot up, like it did in ubuntu and kubuntu.

Im back to ubuntu, 

thx tgilber1
i will try the backup, will save many time, i will try installing K3B and Knotes and see how it works, the autohide like SparklingWater say it leaves some pixels, not fully autohide

thx Landrovan
i will try the next time i use kde, dont know how i miss it, never cross my mind that setting was in mouse, i look all over and only in d3lphin

thx SparklingWater
i find out how to reduce the pixeles and if make transparent it barely notes, what now i hate is that when the panel not expand it leaves 2 white bars at the sides, i think is for the theme ubuntu use, but dont know how to change it

I think i will stay with ubuntu until i find out, or someone tell me how, make the files from a cd get copied with read & write permissions on home

---

### Post by swinky on 2008-01-03
> Unfortunately, GNOME does not fully auto hide the bars. It still shows like 3 pixels.

Actually, this is not entirely true. By default, GNOME's autohide function leaves some visible pixels. This can be changed, but not in the Panel Properties box.

Open up your terminal and type ```
gconf-editor
``` (NOTE: Don't use sudo. The gconf-editor is run on a per-user level, and if you run it as root you won't actually be changing any settings!) This opens a huge list of configurations for various applications. I wouldn't mess with too much in here unless you really know what you are doing.

On the left hand side is a hierarchical list of folders that all the settings are in. Navigate your way down to /apps/panel/toplevels. In this folder you should see a subfolder for every panel you have. For example, since I have the default panels at the top and bottom, there is one called "bottom_panel_screen0" and one called "top_panel_screen0". Yours may be called something slightly different. If you click on the desired panel's folder, a number of entries will appear in the box on the right, such as "auto_hide" and "enable_animations". These are all your settings for your panel.

The important settings in this case are:
auto_hide: You can change this in the panel property, too, but just make sure that the box is checked.
auto_hide_size: This number is how many pixels are shown when a bar is "hidden" Change it to 0 and the bar will be *truly* hidden.
hide_delay: This is how fast (measured in milliseconds) the panel hides itself after you move the mouse away from it. I find the default of 500 to be too long, but it is all personal preference. Set it to whatever value you like.
unhide_delay: This is how fast (again in milliseconds) the panel appears when you mouse over it. Again, set this to your heart's desire.

Change these settings to whatever you like for each panel you have. You can even have different settings for different panels. For example, I have the value for unhide_delay set to 200 for my top bar, but 0 for the bottom. Mess around with these settings until you find something you like!

---

### Post by AlesUbu123 on 2008-01-05
> **swinky said:**
> 
auto_hide_size: This number is how many pixels are shown when a bar is "hidden" Change it to 0 and the bar will be *truly* hidden.

I disagree with the "*truly* hidden" part. Even after changing settings in the gconf-editor, a line consuming about one pixel of my screen is visible at the border where the panel is hidden. This is not a case in KDE.

---

### Post by swinky on 2008-01-05
> Even after changing settings in the gconf-editor, a line consuming about one pixel of my screen is visible at the border where the panel is hidden.

If you want to get all technical, I suppose there is a thin line at the border. But personally, it is good enough for me. I've never liked KDE but was considering switching to a KDE desktop simply because by default the GNOME panels "hide" with a whopping 6 pixels showing. That is hardly hiding, and it drove me nuts. Plus, after changing the settigns in gconf-editor, the panel still shows less than WinXP when autohidden.

---

### Post by Faud on 2008-01-05
```
gnome-session-remove gnome-panel
```

will totally remove the panel if you want and

```
gnome-panel
```

will bring it back

---

### Post by SOULRiDER on 2008-01-05
Ive used both KDE and GNOME a lot and I think KDE is far more customizable than GNOME byt GNOME IMHO offers sort of a cleaner look.

---

