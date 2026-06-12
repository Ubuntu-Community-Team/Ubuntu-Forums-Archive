---
title: "For the love of icons"
date: 2008-12-16
forum: General Help
---

### Post by b4t3m4n on 2008-12-16
I have used linux off and on for many many years.  Games are the only thing that drag me back, kicking and screaming the whole way I might add.

One reason I like linux is the ability to completely customize ever aspect of your desktop.  I am pretty good at it now, but one thing I always fail at is finding icon sets that are complete and scalable.

I have been using gnome lately, and I am struggling to find good icons yet again.  I know there are many sets on gnome-look but I always have several hangups using the sets there.

For starters, can gnome support 100% SVG icons everywhere?  If so, why do icon sets not just use them everywhere?  Secondly, when I install an icon pack via gnome's appearance utility, where does it store those icons at?

Lastly, everyone's AVN always looks incredible, with perfect icons and themes.  Where do I find these themes?  Also, does it really come down to picking icons by hand there since the icon packs always seem to be missing applications.

---

### Post by Locutus_of_Borg on 2008-12-16
i use this icon theme for every linux install i have: [http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619](http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619)

i like it well but it all depends on taste, dont see why it couldnt support .svg, but why not use .png when you can?  easier to modify a .png with gimp than a .svg in inkscape

icons are stored in /usr/share/icons

and yes you do sometimes have to rename, copy over, or otherwise modify a theme's icons to get them just right.

---

### Post by Wartender on 2008-12-16
actually mine are in ~/.icons (you have to press ctrl+h in your home fodler to show icons) just in case yours aren't in usr/share/icons.

and i love [this]("http://www.gnome-look.org/content/show.php/hydroxygen_iconset?content=88575") icon set, because it comes with a shell script to customize it, and since i don't consider it perfect, i have modified the shell script and added other icons from different sets to make it suit me.

---

### Post by Ivo Moelans on 2008-12-16
When yo install an icon theme with Appearance Preferences it stores it locally in */home/<username>/.themes/*.
Gnome supports 100% svg icon themes and there are a few on [http://www.gnome-look.org/]("http://www.gnome-look.org/"). But as far as I understand svg's are  *usually* used to design  the icons. Then they are transformed into png's because those are smaller files and so are easier to handle. Although I also understand that there are different opinions: some prefer png's, some svg's. And svg's are not that difficult to modify in Inkscape. It's like with every application: you have to learn the basics.

About missing icons: it is probably impossible to put an icon for *every* application in a theme. That's why most themes have a fall back theme defined from which missing icons are retrieved; In gnome this is typically */usr/share/icons/gnome* and */usr/share/icons/hicolor*. The last theme is also used by certain programs to dump their icons in when you install it. So it becomes available for the system. Other place their icons in */usr/share/pixmaps* and some place them in their own directories, usually under */usr/share*.
You can always try to hunt down another version of an application icon or make one yourself, give it the appropriate name and put it in your own icon theme.
Not only the main icon but also the icons used *by* the application, like the little *pins* and the *notes* in *TomBoy* can be changed and put into your theme. The icons used by the *clock applet* (see screenshot) can be modified or replaced in */usr/share/gnome-panel/pixmaps*.

As you can see: there are many possibilities. I am sorry to say that there is not much documentation. The best way to learn is to copy a theme to your Desktop and dissect it, change it and see what is does...

---

### Post by Ivo Moelans on 2008-12-16
Forgot the screenshot.

---

### Post by b4t3m4n on 2008-12-16
Okay, things are getting a bit more on track, but I still have a snag.  I am using AWN and what really kills its look is when an icon from a 3rd party app pops its head in there and is using its proprietary icon.

Teamspeak is a good example of this.  I tracked down the /usr/share/teamspeak.xpm file and copied over it with an icon of my choice and now that icon is showing up in all the gnome menus, great!  But, when I run the program, the old crappy icon is still showing up in AWN.  What gives?  I thought it might a cache thing so I rebooted, still uses the old icon for the task :/

---

### Post by Wartender on 2008-12-16
i usually have to change the icons manually in AWN, just right-click it and click change icon

Sometimes this can be pretty nifty though, i have different icons for all my firefox things (thanks to the options of the hydroxygen iconset), one for the actualy browser, one for the downloads, one for the history, etc.

---

### Post by Ivo Moelans on 2008-12-16
I don't use either of those apps, so I can't be of much help here. But you could do a search where Teamspeak has installed itself. In the terminal type: *whereis <appname>*. Then look in all the locations and the subdirectories.
You could also try to put your custom icon in your own theme under */home/<username>/.icons/<IconThemeName>/scalable/apps*. If the theme has no scalable directory, put it in *.../128x128/apps* or the directory that conforms with the dimensions of your icon.

---

