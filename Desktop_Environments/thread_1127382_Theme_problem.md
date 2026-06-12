---
title: "Theme problem"
date: 2009-04-16
forum: Desktop Environments
---

### Post by Ruse on 2009-04-16
Hey dudes and dudettes!
I have this irritating problem that seems impossible to solve. Thing is that I am rather new to Linux and Ubuntu and I really want to change the theme since I am a sucker for eyecandy;). So anyway, Ive learnt that you are supposed to take the tarball that you download from say [www.gnome-look.org](www.gnome-look.org) and drag it into the appearances window without unpacking and the theme should pretty much install itself, so I do that but only a small portion of the theme work like scroll-bars and such but no icons or pointers and so on? The appearance-window tells me that the theme wont look as it supposed to because I dont have the gtk icontheme "" installed? Or sometimes the right gtk themeengine "" installed? What do i do? Am I missing some sort of program or engine? I installed my Ubuntu through this internet site: [http://wubi-installer.org/](http://wubi-installer.org/) and not a cd, could that be a part of the problem maybe?


PS.
One theme that I really want to install is the Gaia Nova, found at: [http://www.gnome-look.org/content/show.php/Gaia+Nova?content=75930](http://www.gnome-look.org/content/show.php/Gaia+Nova?content=75930)
Anyone feel like explaining how to in detail for me?

---

### Post by Therion on 2009-04-16
Well you are correct in that dragging and dropping the tarball onto the Theme Manager will install MOST themes correctly.  Most.  

If you get the message that the theme will not display correctly because you do not have the, for instance, Pixbuf, engine installed then yes, you need to install a specific rendering engine (there are several).  Same for the icon theme.  Some themes will suggest a particular icon theme (icon themes are separate from GTK themes) and would need to be installed separately.  

To confuse matters further, some themes ONLY modify things like the toolbars and sliders; leaving your Window borders and such unchanged.  It all depends on the theme.

In looking at the theme you've linked to, that should work with just a Drag and Drop of the downloaded tarball.  If the theme is suggesting specific engines or icon themes, you'll need to post which ones, specifically, so we can help you install them.

EDIT:  In looking at your Gaia theme, I notice there are three downloads for it.  The GTK component, the Metacity component and a GDM (Login Window).  You'll need to download the first two, at least, and if you want the matching login window, all three files.  The first two are drag and drop onto the Theme Manager.  The GDM is a little different.

---

### Post by Ruse on 2009-04-16
Ok, so i search in Synaptic for gtk and the other engines but i get a list of like hundreds of different things, wich do i have to download?
Btw, Therion, you wanna explain a bit about the GDM?

---

### Post by mcduck on 2009-04-17
Install the engine that the theme manager tells is missing.

If the error in theme manager, for example, says that it's missing engine "murrine" you need to install a package called gtk2-engines-murrine.

You should also note that the theme manage has a small bug that causes it to give meaningless error about missing engine "" (no name for the engine). You should juts ignore this error, nothing is actually missing and your theme works just like it was designed to.

Then to make things about Ubuntu themes a bit more clear, there are several separate types of themes that affect different parts of your user interface. Even though most of these theme types may be distributed in one package, most theme packages only contain one type of theme, and even themes that include all parts often come as separate downloads. In other words it's quite rare that installing a single package would give you a new theme that affects everything.. Most of the time you need to combine different parts yourself.

GTK2 themes change the way your programs look like, your colors, scrollbars, buttons, menus etc.

Metacity themes change window borders & title bar.

Icon themes change your icons.

(If you are using Emerald instead of Metacity you of course use Compiz/Emerald themes instead of Metacity themes to change your window borders).

GDM themes are for the login screen, and they are installed through System/Adminsitration/Login Window. (Go to Local-tab, click "Add" and find your theme archive to install it)

Screensaver themes change the login dialog you get when you lock your screen. These are bit harder to install since there is no tools for the purpose, you just need to extract everything to right place and then use gconf-editor to enable the theme. But the theme packages will pretty much always include detailed instructions how to do this.

Rest of the stuff available in Gnome-look is themes and splash screens for specific applications etc.

---

