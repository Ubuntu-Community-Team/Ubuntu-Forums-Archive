---
title: "How to make GTK Apps Look Better?"
date: 2011-02-04
forum: Desktop Environments
---

### Post by RJ12 on 2011-02-04
Hi guys, finally got to try out the new KDE 4.6, but the problem is, if I want to run a GTK app, it looks like Windows 98. Is there a way to fix this? I thought that this was one of the new features of KDE?

---

### Post by oldos2er on 2011-02-04
Check System Settings, Application Appearance, GTK + Appearance to tweak the settings.

---

### Post by ankspo71 on 2011-02-04
Hi,
Try installing 'oxygen-molecule'. 
> Package description: GTK+ theme to match the Oxygen widget style. Oxygen-Molecule is a theme for GTK+ applications to provide
a uniform look when used under the KDE desktop environment, as long as the Oxygen style is used.
Hope this helps.

---

### Post by RJ12 on 2011-02-04
Unfortunately, those solutions are not working :(

---

### Post by Zorael on 2011-02-04
You installed KDE ontop of an Ubuntu installation, right? This happens when you don't install [**kubuntu-default-settings**](apt://kubuntu-default-settings).

Mind that installing this will apply the Kubuntu branding, so you'll have to reset your plymouth splash screens etc back to Ubuntu's if you don't want the gears.
```
$ sudo update-alternatives --config default.plymouth
$ sudo update-alternatives --config text.plymouth
$ sudo update-initramfs -u -k all
```

Also see [oxygen-gtk](http://hugo-kde.blogspot.com/2010/11/oxygen-gtk.html).

Semi-related;
> @Thomi Richards: "Qt apps look terrible in a GNOME session."

the #1 reason for that is the GNOME developers and to a lesser extent the packagers who often work on packaging GNOME envs up for their distros. they usually don't care much about anything that doesn't come from their own world. there are exceptions, but they are indeed just that: exceptions. the results are indicative of the mindset, and Mark's blog entry is not far from that status quo approach.

in Qt we've done all sorts of useful things such as the platform plugins for environment dialogs (file, print, etc), theme bridges (so, e.g., Gtk+ can theme Qt), dynamic dialog button re-ordering, etc.

in KDE, we have ourselves worked on extending our "native" look 'n feel over to Gtk+ apps with efforts like the Gtk+ Oxygen theme, Firefox and Open Office bridges, etc.

we've adopted (and participated in) icon naming specifications, etc.

and yet .. it's still so very much a one-way street.

so while a Qt (or KDE) app can look quite good in a GNOME env, it sometimes falls short and is made so much harder than necessary.

it's amazing how much a typical Qt or KDE dev tends to know about the available compatibility efforts versus how much the typical Gtk+ or GNOME dev does. i'm constantly unpleasantly surprised when i find yet another Gtk+/GNOME dev or packager has no idea Qt supports native Gtk+ theming, for instance.

Qt 4.7 is far, far better at this than previous releases, but we need people from outside of the Qt and KDE world to start caring more about the _whole_ experience from the user's POV to make it as good as it could, and should, be.

the hermetic sealing of communities and the approach of "here, just use our stuff we developed by ourselves over here and then there's no more problems!" really needs to stop.
[Source](http://aseigo.blogspot.com/2011/01/qt-acceptance-growing-next-colaboration.html)

---

### Post by Copper Bezel on 2011-02-04
I don't understand the sentiment there. It seems like desktop integration is something that individual apps could take care of. If a developer wants to make a package play nicely with both GTK and KDE, he or she is free to do so. If KDE can also work with GTK-centric packages by sheer faking, then that's a perk for KDE users, but ideally, the best user experience is a unified one.

---

### Post by inobe on 2011-02-04
conanical is moving to qt.

---

### Post by RJ12 on 2011-02-04
> **Zorael said:**
> You installed KDE ontop of an Ubuntu installation, right? This happens when you don't install [**kubuntu-default-settings**](apt://kubuntu-default-settings).

Mind that installing this will apply the Kubuntu branding, so you'll have to reset your plymouth splash screens etc back to Ubuntu's if you don't want the gears.
```
$ sudo update-alternatives --config default.plymouth
$ sudo update-alternatives --config text.plymouth
$ sudo update-initramfs -u -k all
```

Also see [oxygen-gtk](http://hugo-kde.blogspot.com/2010/11/oxygen-gtk.html).

Semi-related;

[Source](http://aseigo.blogspot.com/2011/01/qt-acceptance-growing-next-colaboration.html)


I did install KDE on top of Ubuntu, it says that I have kubuntu-default-settings already installed to the newest version.

---

### Post by RJ12 on 2011-02-05
I got it working!! I had to follow the steps [here]("http://kubuntuforums.net/forums/index.php?topic=3115432.0")

I needed to make a .gtkrc-2.0 file and download oxygen-gtk from KDE Look

---

### Post by ankspo71 on 2011-02-05
Hi RJ12,
If you ever consider something other than oxygen for a theme...
I'm using 'qtcurve' for my KDE desktop. It themes my gtk, kde, qt, and mozilla apps quite nicely. I made a screenshot here: [http://i54.tinypic.com/1zgs2h.png](http://i54.tinypic.com/1zgs2h.png)
(sorry about the low quality image)

Qtcurve can be installed with kpackagekit and Synaptic, etc

You can then enable, apply, and import Qtcurve themes by going to:
System Settings > Application Appearance > Style. 
(click on the configure button to import and modify qtcurve themes)

In order for GTK (and mozilla) apps to get themed correctly with qtcurve, you will need to go to:
System Settings > Application Appearance > GTK+ Appearance > Widget Style; and select Qtcurve in the dropdown menu. 

You can then choose the qtcurve window border at:
System Settings > Workspace Appearance > Window Decorations.

On a side note: I really like the Oxygen theme, but I've always had trouble with firefox not wanting to show the gradient part of the Oxygen theme.
Hope this helps.

---

### Post by markthekdeguy on 2011-02-07
i know its solved but just for info, and any new readers,
Kubuntu (by default) installs a QT-GTK engine,
which forces GTK apps to look nice in KDE. lovely even.

installing ' gtk-chtheme '
(and perhaps installing all the 3 or 4 qt-curve bits too maybe)
adds a nice separate GUI into KDE's 'system' sub-menu
which then easily allows you to choose, preview and apply
a huge (if you install them all !) selection of styles to GTK apps, 
making them fit into KDE. nice.

The Qt curve theme stuff is a nice, logical and complete
project aimed at making GTK and QT apps look great together.

So you could set KDE to use qt-curve, and gtk apps
to use the qt-curve theme too, and then it really can be hard
to tell KDE apps from not. plenty of cool tweaks and a bit of 
UI eye candy too.

---

