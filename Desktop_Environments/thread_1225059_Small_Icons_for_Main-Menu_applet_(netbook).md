---
title: "Small Icons for Main-Menu applet (netbook)"
date: 2009-07-28
forum: Desktop Environments
---

### Post by orbish on 2009-07-28
Hello everyone.

I'm trying to shrink the icons within the main menu.  I'm on a netbook and could see other people finding this useful, since vertical on-screen real estate is scarce(1024x600).  There used to be a way to do it back in the day by editing the .gtkrc file, but it doesn't seem to work anymore.  I've edited out as many parts of the menu to make it as small as possible, but it's still not what I'm looking for.

Fonts aren't the issue, the old fix was changing the size of the icons.  Are there any fixes for this?

Screenshot:
[IMG]http://img.photobucket.com/albums/v507/orbish/Screenshot-6.png[/IMG]

I'd like to get the icons on main menu around the size of the icons in the panel.

---

### Post by orbish on 2009-07-28
lumps mumps and bumps

---

### Post by Brandon Williams on 2009-07-31
I took a quick look at the code, and I think the icon sizes are hard-coded into the app. This applies both to the menu icons in the left-hand sidebar and the application icons in the center.

---

### Post by CokeDealer on 2009-10-16
I found that what you want depends on the gtk theme you're using. Some allow to reduce the size of the menu, some don't. Maybe it's something that can be modified using code, but I have no idea how.

I'm using Moka ( [http://gnome-look.org/content/show.php/Moka?content=111979](http://gnome-look.org/content/show.php/Moka?content=111979) ), which is the first theme I've used that allows icons as small as a 9-size font.

Another thing you can try if you dislike the lack of customization of the suggested gtk theme (although for that you can use Gnome Color Chooser, it's in the repos) is remove the icons from the menu. At the time I'm still figuring out how I did it, but doing such removes the ability to recognize an item in the menu much more easy than reading the names or getting used to a location.

Something else you might like for optimization of space in your netbook is, again, using Gnome Color Chooser, because it allows to reduce the width of scrollbars, simplify buttons by using different window engines for specific things, among other stuff.

And (in my opinion) to give a better use to that gnome panel you're using you may like globalmenu-panel-applet. It steals the menu bar from gtk apps and puts it in the panel. Of course, not all the apps allow this, but for gnome-native applications, it has proven to be really comfortable for me.

[IMG]http://i717.photobucket.com/albums/ww180/CokeDealer/desktop.png[/IMG]

---

