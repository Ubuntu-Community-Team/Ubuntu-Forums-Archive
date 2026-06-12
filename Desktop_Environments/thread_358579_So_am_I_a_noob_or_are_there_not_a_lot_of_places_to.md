---
title: "So am I a noob or are there not a lot of places to find themes?"
date: 2007-02-11
forum: Desktop Environments
---

### Post by SnowPunk98 on 2007-02-11
I am quite new to Ubuntu however I have it setup and running nicely. I am now just trying to give it a feel so that it feels like home. There are a lot of things that I have seen so far in my search and I'm not sure which I actually need. 

If I want to change the whole look and feel of my UI is it a GTK 2.x replacement I am looking for? Any help in this direction would be appreciated. Sorry for the dumb question I have searched these forums and Google for a while.

---

### Post by taurus on 2007-02-11
[http://www.gnome-look.org](http://www.gnome-look.org)

---

### Post by ardchoille42 on 2007-02-11
[http://art.gnome.org](http://art.gnome.org) also has a nice collection.

---

### Post by 3rdalbum on 2007-02-11
If you are running Gnome, then there are two things you'll want to find and change:

GTK 2 theme
Metacity theme

Metacity controls the borders of the windows.

Some GTK themes come with Metacity themes as well as desktop backgrounds and themes for other window managers.

---

### Post by komitski on 2007-02-11
Sorry, for my stupid question, but I'm very new here and I want to start Ubuntu.
Where I can start first, thanks.

---

### Post by _simon_ on 2007-02-11
Theming resources: [http://www.violet-rain.info/](http://www.violet-rain.info/)

---

### Post by trippinnik on 2007-02-11
the best thing i've found is to use Art Manager.  You can use Synaptic under the System->Administration menu.  Search for art manager it should be listed as a package to install.  when you run this program it can grab themes, backgrounds, login themes etc and gives you previews then you can install them from there too.  you may also want to try other desktop environments.  ubuntu uses Gnome by default which I love, but there are so many choices.  KDE (very popular), Enlightenment, Fluxbox, Openbox, RoxBox, xFCE and more.

---

### Post by SnowPunk98 on 2007-02-11
Art Manager is great, thanks a lot for that suggestion. I have my system looking and feeling good now :)

---

### Post by liljoe76 on 2007-02-11
Originally Posted by jordanmthomas  

    * GTK 1.x -- old Gnome programs. You will probably not want to use these unless you like old themes
    * GTK 2.x -- Gnome application controls, and your panel, etc. These change the overall look of Gnome
    * Metacity -- The window borders -- title bar, min / max /close buttons, etc.
    * Compiz -- a composited (accelerated) window manager. These are window borders for compiz (if you don't know what it is you don't have it installed) ( [http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz) )
    * Beryl -- beryl is a fork of compiz and these are also window border themes. Like compiz, this is not installed by default in Ubuntu ( [http://beryl-project.org](http://beryl-project.org) )
    * Icon Themes -- The icons used in GTK apps. Look around at all your icons. These themes will change those icons
    * GDM Themes -- logon screen themes
    * Splash Screens -- Screens similar to what you get when you log in (loading panel...etc), or when you start OpenOffice (start it and you'll see what I am talking about)
    * Desklets -- themes for a program called gDesklets (not sure if it installed by default in Ubuntu)
    * XMMS Themes -- XMMS is an old media player. These are themes for it
    * Screenshots -- Screenshots people have posted (you won't be able to see them by default as screenshots are filtered at gnome-look
    * Fonts -- these you can install by placing them in ~/.fonts
    * Cliparts -- I believe these are just random little pictures you can use for various purposes


art.gnome.org gives some more categories, a bit less confusing:

    * Desktop Themes -- Wallpaper
    * Application -- GTK 2.x themes
    * Window Border -- metacity themes
    * Icons -- Same as at gnome-look
    * Login Manager -- GDM
    * Splash Screen -- The screen you see after logging in but before you are 100% ready to use your computer
    * GTK+ Engines -- some themes rely on these engines. If you install a GTK theme that doesn't look like what you expected you will want to see if it relies on a particular engine. If it does, you can probably get it here



In case you didn't know, you generally install themes by dragging the .tar.gz on to the window that comes up if you go to System --> Preferences --> Theme
If it complains, you will have to manually extract the contents of the tarball into ~/.themes (for GTK themes and metacity) ~/.icons (for icon themes)
Anything other than GTK, metacity, and icon themes must be installed using the appropriate program. ie you would use XMMS to install XMMS themes
[http://ubuntuforums.org/showthread.php?t=349408](http://ubuntuforums.org/showthread.php?t=349408)
i found this post informative. thx for the violet rain link.
good stuff, 
joe

---

### Post by ardchoille42 on 2007-02-11
Just a tip. If you install a multi-theme tarball using the gnome-theme-manager installer, it will only install the first theme from the tarball. The installer has problems with multi-theme tarballs. If you are finding this to be the case, then it's a better idea to unpack the theme tarball into either ~/.themes (one user only) or /usr/share/themes (system wide).

---

