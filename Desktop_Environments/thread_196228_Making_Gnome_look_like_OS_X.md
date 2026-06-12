---
title: "Making Gnome look like OS X"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Trocisp on 2006-06-13
Preface:  Today a friend said that he loved apple, and in 3 months is going to get an apple - but not because of security or being a "*mac culty*," but because he likes the way it looks.  So he told me he'd give me 20 bucks if I could skin a standard installation of any unix/linux os to look like it and save him the difference in cash.  I (of course) took the bet and said I can make ubuntu look nearly the same, so close that the extra 500 USD for the Mac wouldn't be worth it.

My final goal is to make it look like [this](http://users.utu.fi/ljtaim/images/after_big_1.jpg).  Currently I have gDesklets for the launcher bar (I may change that for a Gnome bar - but I'll have to figure out how to customize that so when you maximize the window it covers the bottom gnome bar).

This is the part I need help on:  
For now I need to figure out how to change the Gnome bar at the top of the screen to have the OS X looking background.  I also need to find a decent folder theme.

Any help would be great, thank you.  :)

Oh, and I've tried [this](http://users.utu.fi/ljtaim/ubuntuosx.php) guide, It was good, but as said, incomplete.

---

### Post by aysiu on 2006-06-13
You know, when your friend says he likes the way it looks--is he talking about the general Aqua interface and the icons? Or does he actually like how well-integrated the graphics are and how smooth the animation is?

I know on Ubuntu you can get something like Expose, the Dock, the Aqua interface, the Mac icons, etc., but sometimes it looks rather sloppily patched together, and the smooth animation seems to be out of the picture--particularly for Expose and Dock stuff.

---

### Post by tigrux on 2006-06-13
Try Glossy P as your gtk theme,  starterbar gdesklet, and OSX icons.

---

### Post by Trocisp on 2006-06-13
[QUOTE=tigrux]Try Glossy P as your gtk theme,  starterbar gdesklet, and OSX icons.[/QUOTE]Would you mind providing me with a place to download some OS X icons?

---

### Post by Trocisp on 2006-06-13
Anyone, please? :(

---

### Post by aysiu on 2006-06-13
Try [here](http://www.gnome-look.org/content/show.php?content=31618).

---

### Post by Trocisp on 2006-06-13
[QUOTE=aysiu]Try [here](http://www.gnome-look.org/content/show.php?content=31618).[/QUOTE]
[http://uploads.trocisp.com/desktops/June13%202006.png](http://uploads.trocisp.com/desktops/June13%202006.png)

This is where I'm at so far.

---

### Post by Ahriman on 2006-06-14
Whilst it's been ages (read: years) since I've used KDE, I always thought it came with an OSX-like theme. I know that it has the ability to have an OSX-like menu bar, but I could have sworn it had the theme as well.

As always, I stand(sit) ready to be corrected, but that is one option you could take.

---

### Post by aysiu on 2006-06-14
It's called *kwin-baghira*, and it's available in the repositories.

---

### Post by Trocisp on 2006-06-14
[QUOTE=aysiu]It's called *kwin-baghira*, and it's available in the repositories.[/QUOTE]That's an option then... but my hope is to make this work on gnome, because I'm framiliar with gnome. heh

---

### Post by msandersen on 2006-06-14
Looking good so far. I tried the OSX icons back on Breezy. I like it. Seems it's been updated.
There has been at least 2 articles on Wired about Faux Macs, mostly Windows users going to extremes to theme their PCs to look like Macs (Windows has to be hacked to allow 3rd party themes). Various companies provide theme engines and other software, like the Dock complete with the animations. Apparently OSX themes are consistently among the top themes for both Windows and Linux and Firefox.

Maybe you can make a how-to on your implementation when done, or list what you've used here with links for others. :razz:

**PS:** A similar, if not the same, Safari-like Firefox theme on the official theme site and Deviant Art, iFox, also showed how to get the rounded corners on the Location bar. You have to edit 
```
~/.mozilla/firefox/[randomstring].default/chrome/userChrome.css
```
and put
```
@import url("chrome://global/skin/subskin/rounded.css");
```
before the **@namespace** line, ie so you have
```
@import url("chrome://global/skin/subskin/rounded.css");
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
```
That's what I use right now.

**PPS:** Putting the bottom panel up top doesn't look good, and makes it cluttered. One of the reasons I prefer Gnome. Just my opinion. It's never gonna be 100% anyway.

---

### Post by ayoli on 2006-06-14
[QUOTE=Trocisp]That's an option then... but my hope is to make this work on gnome, because I'm framiliar with gnome. heh[/QUOTE]
if you want to use baghira deco on gnome use the gtk2-engines-gtk-qt which is available in repositories, then set your gtk theme thru kcontrol

---

### Post by msandersen on 2006-06-14
As I understand it, gtk2-engines-gtk-qt is for KDE users who want GTK apps to look more like QT apps. It renders the windows with QT instead of GTK. So I don't think it allows you to use a KDE theme in Gnome.

---

### Post by kvonb on 2006-06-14
Looking at the two pictures, the most appealing thing in my opinion is drop shadows!

Adding those would bring your modofied theme to life, the only problem is that you will have to wrestle with XGL/Compiz to get them!

---

### Post by ayoli on 2006-06-14
[QUOTE=msandersen]So I don't think it allows you to use a KDE theme in Gnome.[/QUOTE]
ugly but works :p

---

### Post by kvonb on 2006-06-14
Oh yes,

And to get the top menu bar looking like the pic of the os/x, just use gimp to cut out a chunk from that pic, save it, right click on the menu bar, background, then use that cutout as your background :)

---

### Post by kvonb on 2006-06-14
This is a quick attempt using the crop from the pic you provided.  I use gdesklets for the clock, weather, net, hdd, and groovy launcher bar on the right.

Theme:
Controls: Glossy P
Window Borders: evil_mac
Icons: ChaninDjoole

All from gnome-look.org

No drop shadows though :(

Thanks to "Artificial Intelligence" from whom I copied this desktop theme :D
(well they say that copying is flattery ;) )

---

### Post by GadgetsGuy on 2006-06-14
[QUOTE=kvonb]This is a quick attempt using the crop from the pic you provided.  I use gdesklets for the clock, weather, net, hdd, and groovy launcher bar on the right.

Theme:
Controls: Glossy P
Window Borders: evil_mac
Icons: ChaninDjoole

All from gnome-look.org

No drop shadows though :(

Thanks to "Artificial Intelligence" from whom I copied this desktop theme :D
(well they say that copying is flattery ;) )[/QUOTE]
looking VERY nice kvonb!

I will keep my eyes on this thread! ;)

---

### Post by Hanj on 2006-06-14
Did you try [this]("http://www.gnome-look.org/content/show.php?content=13548") theme? I has detailed instructions on how to get both windows and icons to look  like OSX. Add xcompmgr for some drop-shadows and Engage for the starter bar, and you should be pretty close.

---

### Post by Rondonjin on 2006-06-14
[QUOTE=Trocisp][http://uploads.trocisp.com/desktops/June13%202006.png](http://uploads.trocisp.com/desktops/June13%202006.png)

This is where I'm at so far.[/QUOTE]

Now fire up Gconf Editor and go to apps > metacity > general and look for the 'button layout' entry. Change it from:

menu:minimize,maximize,close

to:

close,maximize,minimize:menu

and your buttons will be on the left.

Wayne

---

### Post by arrizaba on 2006-06-14
Why don't you try one of the T-ish themes? 
At work I have the T-ish brushed theme and it always fools people thinking that I have a Mac Mini somewhere hidden... ;) 

You can get it at gnome-look.

Brushed version (the one I use):
[http://www.gnome-look.org/content/show.php?content=30972](http://www.gnome-look.org/content/show.php?content=30972) 

Normal version (it works with clearlooks-cairo to get animated progress bars and so on, like the bars in MAC OS X's Aqua):
[http://www.gnome-look.org/content/show.php?content=30859](http://www.gnome-look.org/content/show.php?content=30859)

They even have a Compiz version:
[http://www.gnome-look.org/content/show.php?content=39324](http://www.gnome-look.org/content/show.php?content=39324)

Other goodies:

MAC OS X Icons (they are identical to the Mac's):
[http://www.gnome-look.org/content/show.php?content=31618](http://www.gnome-look.org/content/show.php?content=31618)

Adesklets or Gdesklets: For "Dashboard"-like features.

If you want your Desktop to look like MAC OS X you should definitely install either Xgl+Compiz or AIGLX+Compiz (for NVIDIA/ATI or Intel graphics cards, respectively). Then install the brightside package to activate an Expose-like feature when you move your mouse to the corner of the screen. See:
[http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)

Compiz plus the themes and icons above will make your Linux computer look like a Mac. Trust me, I own a Mac and a Linux PC, and the desktop looks the same :D

---

### Post by Trocisp on 2006-06-14
[QUOTE=msandersen]Looking good so far. I tried the OSX icons back on Breezy. I like it. Seems it's been updated.
There has been at least 2 articles on Wired about Faux Macs, mostly Windows users going to extremes to theme their PCs to look like Macs (Windows has to be hacked to allow 3rd party themes). Various companies provide theme engines and other software, like the Dock complete with the animations. Apparently OSX themes are consistently among the top themes for both Windows and Linux and Firefox.

Maybe you can make a how-to on your implementation when done, or list what you've used here with links for others. :razz:

**PS:** A similar, if not the same, Safari-like Firefox theme on the official theme site and Deviant Art, iFox, also showed how to get the rounded corners on the Location bar. You have to edit 
```
~/.mozilla/firefox/[randomstring].default/chrome/userChrome.css
```
and put
```
@import url("chrome://global/skin/subskin/rounded.css");
```
before the **@namespace** line, ie so you have
```
@import url("chrome://global/skin/subskin/rounded.css");
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
```
That's what I use right now.

**PPS:** Putting the bottom panel up top doesn't look good, and makes it cluttered. One of the reasons I prefer Gnome. Just my opinion. It's never gonna be 100% anyway.[/QUOTE]It's the little things that contiribute to the overall theme.

---

### Post by msandersen on 2006-06-14
The guide he was going by used the T-ish theme for Clearlooks and the OSX icon theme set, iFox for Firefox, and the Composite Manager based on a guide by Poofyhairguy on these forums.

---

