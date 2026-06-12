---
title: "Trying KDE after a long time..."
date: 2005-09-19
forum: Desktop Environments
---

### Post by audax321 on 2005-09-19
Hello,

      I want to install Kubuntu on a spare computer, but had some questions about it. It's been a long time since I've used KDE and I started using Gnome mainly because it  has some nice features such as easy theme installation and a scripts menu in Nautilus.

Things I like about Gnome:
  - /home/user/.themes folder to easily install themes
  - /home/user/.icons folder to easily install icons
  - nautilus has a scripts menu to run scripts on selected files in the file browser

Things I hate about Gnome:
  - Applets on the panels sometimes crash and disappear.
  - If you have a lot of icons on the panels, it is difficult to keep them all arranged because you have to keep doing right click>unlock, right click>move, right-click>lock... etc. etc.
  - Windows open on a random monitor when running dual-screen monitor setup

Things I hated about KDE:
  - had to compile themes to install them and then, how do you remove them if you lose your compiled source and can't do make uninstall?????
  - icons on desktop seemed to have a mind of their own and move around after rebooting
  - KDE has an Actions menu, but how do you actually make and add scripts to it for Konqueror to use????

Things I liked about KDE:
  - SuperKaramba - gDesklets is nice, but I think SuperKaramba had a lot more desklets available for it.
  - Dual screen mode - in Gnome it seems like windows just randomly show up on whichever monitor they feel like. I liked how in KDE the windows opened on the monitor where the mouse cursor was instead - it was a lot more productive because of this.


Basically what I'm asking for are either solutions to the things that I hated about KDE or other reasons why it would be worth my time to try KDE again. I really did like it, but, as I said, the themes installation and lack of a scripts menu in Konqueror kept me from using it.

---

### Post by drizek on 2005-09-19
[QUOTE=audax321]Hello,

      I want to install Kubuntu on a spare computer, but had some questions about it. It's been a long time since I've used KDE and I started using Gnome mainly because it  has some nice features such as easy theme installation and a scripts menu in Nautilus.

Things I like about Gnome:
  - /home/user/.themes folder to easily install themes
  - /home/user/.icons folder to easily install icons
  - nautilus has a scripts menu to run scripts on selected files in the file browser

Things I hate about Gnome:
  - Applets on the panels sometimes crash and disappear.
  - If you have a lot of icons on the panels, it is difficult to keep them all arranged because you have to keep doing right click>unlock, right click>move, right-click>lock... etc. etc.
  - Windows open on a random monitor when running dual-screen monitor setup

Things I hated about KDE:
  - had to compile themes to install them and then, how do you remove them if you lose your compiled source and can't do make uninstall?????
  - icons on desktop seemed to have a mind of their own and move around after rebooting
  - KDE has an Actions menu, but how do you actually make and add scripts to it for Konqueror to use????

Things I liked about KDE:
  - SuperKaramba - gDesklets is nice, but I think SuperKaramba had a lot more desklets available for it.
  - Dual screen mode - in Gnome it seems like windows just randomly show up on whichever monitor they feel like. I liked how in KDE the windows opened on the monitor where the mouse cursor was instead - it was a lot more productive because of this.


Basically what I'm asking for are either solutions to the things that I hated about KDE or other reasons why it would be worth my time to try KDE again. I really did like it, but, as I said, the themes installation and lack of a scripts menu in Konqueror kept me from using it.[/QUOTE]
 you can ussually find debs for kde themes, so you just remove it with synaptic. otherwise, im not really sure. ive never wanted to uninstall one. 

icons shouldnt move around, they dont for me anyway. make sure you dont have any "auto arrange" stuff enabled

 if you mean the rightclick actions menu, those are scripts that you have to write and then put in some folder. ive never made one so i dont know any specifics. you can find some on kde-apps.org or maybe kde-look.org. there is one thats made for ubuntu that lets you right-click install debs. its is worth installing and can be used as a template.

---

### Post by ltmon on 2005-09-20
The "random icon placement" has been a long standing bug that is finally fixed in KDE 3.5 (which is to be released within the next couple of months I think).

Then again, by default Kubuntu doesn't use desktop icons - so this hasn't bothered me....

As for easy location of themes, icons, wallpapers etc. KDE is pretty easy to use with the Control Center modules for each one.  For example the "Icons" control center module has an "Import Icons" button which will then allow you to select a tarball containing an icon theme.  This is automatically put into the right place.

If you prefer the more Gnome-like way of doing it, then this app may help: [http://kde-apps.org/content/show.php?content=26521](http://kde-apps.org/content/show.php?content=26521)

L.

---

### Post by audax321 on 2005-09-20
Nice, I found a tutorial that should make it easy to update my Nautilus scripts to KDE ones: [http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html)

Now, do any of you know if compiled themes are just installed into some theme directory in KDE or are they installed all over the place. If they are just installed in some specific directory (i.e. /usr/share/KDE/themes/<nameoftheme>), I would assume that the directory can just be deleted to remove the theme. I never really felt comfortable having to compile a theme to install it. And yes, themes are available in Synaptic, but there is always that one theme that you can't find but want and that is something that used to annoy me when I used KDE before. I was hoping that theme installation would have been made much cleaner by now.

---

### Post by aysiu on 2005-09-20
That list of gripes pretty much sums up my KDE v. Gnome verdict. Right now, I, too, am going back to KDE after a while with Gnome. There are good and bad things about each one, and I suspect I'll keep bouncing back and forth between them for a while (with the occasional dip into XFCE, too).

---

### Post by drizek on 2005-09-20
most of the themes on kde-look.org do actually have a deb avaiable. you will have to download it manually though because most of them are not available on synaptic.

---

