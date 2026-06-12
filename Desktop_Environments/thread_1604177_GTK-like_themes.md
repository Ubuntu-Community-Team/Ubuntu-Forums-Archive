---
title: "GTK-like themes?"
date: 2010-10-23
forum: Desktop Environments
---

### Post by flxdms on 2010-10-23
Hi,

I have been using Ubuntu for quite a while now. I recently switched from Gnome to KDE (I still didn't remove Gnome completely). So far, I like it very much. The only downside is that, even after searching for quite a while, I haven't been able to find a way to change the actual window theme. I am unable to change my scrollbar/windows color. On gnome, all I have to do is download a GTK theme and go to System > Preferences > Appearance but I can't seem to find anything that lets me do the same thing. Since GTK doesn't seem compatible with KDE, I am struggling to find window themes. I can use Emerald themes just fine. The only Desktop Themes I have found were integrated inside KDE and were Plasma themes, not actual KDE window themes.

Can anyone help me please?

Thank you.

Edit: I am using the kubuntu-desktop kde version, whatever the version is. I think it is 4.5

---

### Post by ankspo71 on 2010-10-24
Hi,
KDE windows technically use theme 'styles' and engines. but Gnome uses actual themes and engines. There are several types of styles that people can choose from, but the most popular are Oxygen, QtCurve, and Bespin. Search for these packages in your package manager to install Qtcurve and Bespin: kde-style-bespin kwin-style-bespin qtcurve. Once you have them installed, you can go to System Settings > Application Appearance > Style: Here you will see a drop-down box that will allow you to choose a different Widget Style. You can choose any you like. Notice the Configure button? Here is where you can configure each style, and/or import a style configuration that you downloaded. Qtcurve and Bespin have more ways to configure their style than Oxygen does. 

If you go to [_KDE-Look.org_]("http://kde-look.org/"), you can find theme styles by clicking on the "Themes / Styles" section on the left side of the page. You can import these styles when you click on the "configure" button like I mentioned above.

Currently my favorite style is QtCurve, because it feels more lightweight, it is very configurable, and it also comes with a qtcurve GTK theme engine that will allow me to have matching themed Gnome applications running inside Kubuntu, which is kind of what you said you are looking for. There is a working '[_Oxygen GTK theme engine_]("http://kde-look.org/content/show.php/gtk-oxygen-engine?content=129715")' out there, but it isn't included in Kubuntu yet. I don't think there is one for Bespin yet. The GTK theme engines for KDE is what that "GTK+ Appearance" category is for in System Settings > Application Appearance > GTK+ Appearance.

You can also have Aurorae themes which are kind of like having the KDE equivalent of Emerald themes in Gnome, but you can have Compiz and Emerald in KDE too if you want to. Theme-ing your KDE desktop is a bit more complex than it is in Gnome, and there are less KDE themes (styles) to choose from, but the configurabilty almost makes up for it. Too bad KDE apps and Gnome apps don't automatically and seamlessly theme well together though.

---

### Post by ankspo71 on 2010-10-24
Hi Again.

If you are having an ugly looking theme problem when you run a GTK program as 'root' in Kubuntu, then I have a few notes that I have taken that should fix this:

> GTK theme fixes for Ubuntu and Kubuntu.

This will fix gtk application themes that run as root
such as Synaptic Package Manager.

In Gnome (Ubuntu):
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts

In KDE (Kubuntu):
sudo ln -s ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0
sudo ln -s ~/.gtkrc-2.0-kde4 ~/.gtkrc-2.0

---

