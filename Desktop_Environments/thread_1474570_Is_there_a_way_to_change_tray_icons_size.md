---
title: "Is there a way to change tray icons size?"
date: 2010-05-06
forum: Desktop Environments
---

### Post by penguin1024 on 2010-05-06
Hello everybody!):P
Is there a way to change the tray icons size? Or to change the tray height?
I want to reduce the icons size.
Thanks  ;)
penguin1024

---

### Post by dino99 on 2010-05-06
right-click -> properties

---

### Post by penguin1024 on 2010-05-06
> **dino99 said:**
> right-click -> properties
Thanks, but I want to change only the notification icons size,not the panel...
  I have attached an image. :p

Thanks again ;)
penguin1024

---

### Post by penguin1024 on 2010-05-07
nobody?:cry:

---

### Post by penguin1024 on 2010-05-09
bump :confused:

---

### Post by penguin1024 on 2010-05-16
Is it impossible? :(

---

### Post by NE Key on 2010-05-16
Change the thickness of the bar  (its height) . The icons adjust.

(Or it did in the 9 versions)

---

### Post by penguin1024 on 2010-05-17
Thanks to everybody
But... it still not the issue of this thread
Please read reply #3 (not the panel,just the icons!! \\:D/)
Thanks again :)
penguin1024

PS: sorry for my very bad English

---

### Post by BrokenKingpin on 2010-05-18
I have the same problem. I increased my panel to 32px from 24px and now the notification area (system tray) icons are huge. I would also like to change just the icon size in the tray (smaller). Any help would be great.

---

### Post by BrokenKingpin on 2010-05-21
bump!

---

### Post by SlidingHorn on 2010-05-21
Well I don't have a solution, but doing some digging, I found [this page]("http://www.mail-archive.com/debian-gtk-gnome@lists.debian.org/msg13382.html").  The only file I saw (didn't dig through all of the .gconf directories) that had mentions of icon scale/position was here:

~/.gconf/apps/nautilus/desktop-metadata/61@32@GB@32@Filesystem@46@volume

**It's not recommended that you edit those files directly**, as you should use the gconf-editor, but I don't know if there's a setting within there for your purposes.

---

### Post by penguin1024 on 2010-06-04
Well,I think it isn't possible to do with Gconf editor.:(
sorry
penguin1024

---

### Post by amoun on 2010-06-07
Yes! I'm bumping this thread.
I want to increase system tray icons on hardy

---

### Post by penguin1024 on 2010-06-22
nobody? :confused:

---

### Post by t.rei on 2010-06-26
I'm kindof looking for a solution myself. I am almost certain, that once I figured out what class/widget_class the notification area is, one should be able to put a line in the theme's gtkrc.

thinking ythickness here.

just a thought.

---

### Post by t.rei on 2010-06-26
Sadly this does [COLOR=Red]not[/COLOR] work. Hm, still trying.

```

style "panel-notif"
{
    ythickness = 12
    xthickness = 12
}
widget_class "*notif*" style "panel-notif"
widget_class "*Notif*" style "panel-notif"

```

---

### Post by t.rei on 2010-06-27
So the thing I ended up doing was to take the status-icons of the app that was annoying me (pidgin being a different size than the same icon for gajim) and creating the 22x22 ones I needed to make it look good.

Now things are fine for me, but sadly I haven't found a way to make it 'right' for you all.

---

### Post by t.rei on 2010-07-07
also fixing the anoyance of the pidgin icon being too large on big panels:

go to: 
/usr/share/pixmaps/pidgin/tray/hicolor/

rename 32x32 to 32x32.bu and create a link to 22x22 called 32x32
same for 48x48:

```

cd /usr/share/pixmaps/pidgin/tray/hicolor/
sudo mv 32x32 32x32.bu
sudo mv 48x48 48x48.bu
sudo ln -s  22x22 48x48
sudo ln -s  22x22 32x32

```reapply the icon theme, and the size of the pidgin tray icon should now be 22 at all times.

---

### Post by floopy1962 on 2010-07-13
hm i'm trying to do the same but i want to make icon to be 48px... 
all of my icons are 48 except the ubuntu one icon... here the screenshot:
 [http://i30.tinypic.com/5bur7d.png](http://i30.tinypic.com/5bur7d.png)
the same with the skype icon but there the icons are in the skype source and skype is not open source... but is there some configuration file i can't edit or with gconf-editor ?
i use xfce4-panel with xfce notification area but with gnome notification area is the same...
i tryed to replace all ubuntu one 24x24 icons with mine 48x48... it use mine but again 24.... maybe i will tryed with .png's
EDIT: with png's doesn't work but i figured it :P i just search with gnome-search-tool for ubuntuone files and find ubuntuone-client-applet in /usr/bin/ and change all 24 size's with 48... now work's :) 
[http://i28.tinypic.com/28lfame.png](http://i28.tinypic.com/28lfame.png)
the xfce notification area has a cool option to hide some icons : [http://i30.tinypic.com/206c4ua.png](http://i30.tinypic.com/206c4ua.png)
Just ignor my reply :P

---

### Post by WinRiddance on 2010-07-13
Find yourself a theme that permits you to make the panel colors either completely transparent and/or one that will match your existing colors. Then resize the panel properties by at least 4 pixels (maybe 6) at a time to increase or decrease the panel with its icons.

**Panel and corresponding icons work together.** The default size is 24. But I don't see why you can't adjust that down to only 18 or less pix _which should at the same time decrease the symbol size_ in the panel too? Who cares what size the panel is if it is transparent or the same color as your background ... ???

You can also right click on each symbol in order to change the properties and image of any symbol. When you look in your icon cache you'll see scalable symbols any you'll usually also see 12 x 12, 16 x 16, 32 x 32, and so on. If you change the properties of an existing symbol to one of the smaller ones then I'd imagine that you'd get a smaller symbol on your larger panel that way too ???
Go to **usr/share/icons** to select new symbols/sizes.

You'll have more choices **if you install additional themes first** since many themes have their own icon packs. Once finished I'd highly recommend installing Ubuntu Tweak (google it) because the panel lockdown in the Gconf editor doesn't work all of the time. The gnome panel lockdown in Ubuntu Tweak works perfectly ....

---

### Post by aeon.flux on 2010-07-13
I have another solution...
You can pick the icon theme that you're using and open it. Open all status icons that are used in tray with GIMP and use "canvas size" to add some transparent pixels to all sides. Then using "scale image" decrease the size of the icons to original and save changes. The icons will look smaller and have some space around itself. So easy...

---

### Post by floopy1962 on 2010-07-14
yea also you can do it with inkscape too ;)

---

### Post by penguin1024 on 2010-07-19
Yes!!!! Good idea, I think it's _the_ simplest solution...:p
Thanks for all ideas!!

penguin1024

---

