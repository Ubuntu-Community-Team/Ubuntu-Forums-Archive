---
title: "Adjust size of launcher icons on panel"
date: 2010-04-21
forum: Desktop Environments
---

### Post by nickzeff on 2010-04-21
Hi,

This should be an easy one, but after much googling I cannot find the answer. _[This thread]("http://ubuntuforums.org/showthread.php?t=475782")_ would indicate that other users may have the same difficulty.

I have a fresh install of Lucid and I am tweaking the appearance. I am using the Ambience theme as my base. I have a panel on the bottom of my screen which is 35px high. My problem is that the launchers for the applications (such as firefox, vlc etc.) are much bigger than I would like when the panel is this size. They seem to scale vaguely depending on the size of the panel, but I would like them to be smaller in relation to the panel.

In an attempt to experiment, I am editing

/usr/share/themes/Ambience/gtk-2.0/gtkrc

to see if I can adjust anything in there. I have tried adjusting the ythickness of the panel style (under style "panel" = "dark"), but with no effect. Perhaps I am putting the value in the wrong place.

I have also tried adding "panel=16,16" to the list of gtk-icon-sizes but this does not have any effect on anything. Adjusting  "panel-menu=20,20" to "panel-menu=16,16" *does* have an effect on my desktop, changing the size of icons in the menu... but I cannot change the icon size on the panel itself.

Any gnome gurus out there have any idea how to do this?

---

### Post by realzippy on 2010-04-21
Can't you make it the dirty way?

Your icons should be in:

/usr/share/icons/Ambience/

in different sizes...can't you delete the big ones and replace them with the smaller ones you need?

---

### Post by nickzeff on 2010-04-21
> **realzippy said:**
> 
Your icons should be in:

/usr/share/icons/Ambience/

in different sizes...can't you delete the big ones and replace them with the smaller ones you need?

Thanks for the reply, realzippy.

Unfortunately, I don't think it's that simple. The icons for the launchers do not reside there. The firefox launcher icon is at /usr/share/pixmaps/firefox.png

I think the png then scales according to the panel size.

As an experiment, I tried replacing the icon with a small image of my own. However, it was just scaled up to fit (and looked horrible!).

---

### Post by nickzeff on 2010-04-24
So I'm guessing no-one knows the answer to this?

---

### Post by Astralnaut on 2010-04-24
Right click panel,click properties,change pixel size.This will also change the size of the panel.

---

### Post by nickzeff on 2010-04-25
> **Astralnaut said:**
> Right click panel,click properties,change pixel size.This will also change the size of the panel.

Thanks for replying, but if you read my post you'll understand that this isn't the problem.

I know I can adjust the size of the panel and the launcher icons on it by going into the properties. However, I want to adjust the size of the icons independently of the panel, since the scaling of the icons within the panel looks ugly to me. They are too large for the height I have set the panel.

---

### Post by nickzeff on 2010-04-27
As an update, it appears that this has been raised as a bug with the gnome developers. It was raised on launchpad... 

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/43232](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/43232)

And then moved upstream...

[https://bugzilla.gnome.org/show_bug.cgi?id=343436](https://bugzilla.gnome.org/show_bug.cgi?id=343436)

It appears a padding property is available in Fedora, but not in Ubuntu...

---

