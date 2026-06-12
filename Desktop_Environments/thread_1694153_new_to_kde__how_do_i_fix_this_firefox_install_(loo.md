---
title: "new to kde:  how do i fix this firefox install? (looks crappy)"
date: 2011-02-23
forum: Desktop Environments
---

### Post by aaronLund on 2011-02-23
Boy do I hate how firefox looks with this dark kde theme?

The question is....Where is all of this 'kde customization' taking place?

It's not a theme.  And I don't see any css files in my /home/aaron/.mozilla/firefox/chrome folder.

I just want a normal firefox.

Also, for some reason, I can't install my standard NASA Night Launch theme either.

Never downloads.  I click 'install' and.....nothing.

My mouse cursor looks so ridiculous as well.

It's downright embarrassing when the wife walks in.

---

### Post by Old *ix Geek on 2011-02-24
Have you gone through the plethora of settings under **Settings | System Settings | Appearance**?

---

### Post by aaronLund on 2011-02-24
Yes, they seem to go from 'dreadful' to 'heinous'.

That's a hard meter to master!

;-)

---

### Post by ankspo71 on 2011-02-25
Hi,
At the firefox addon site, right click and "save as" so you can download the theme yourself to install the theme package offline, without having to use firefox's method of downloading it (which used to give me trouble too). When it is downloaded, you can either right click on the file and say "open with firefox" (not sure if that works with *.jar files though), or you can open the firefox addons dialog and click on the install button. In firefox 4 beta they have an option that says "install add-on from file.." inside that gear button thing on the top right of the addon dialog (see screenshot).

Also, firefox4 beta requires 'gnome-icon-theme' to be installed on your system or else it will have missing icons in the toolbar.

Firefox is neither a KDE, QT, or even GTK technically. I'm reading its interface is made from XUL. Since it is not true GTK it is difficult to theme.  

Kubuntu only comes with one GTK theme engine so for some people it is necessary to install additional gtk theme engines for KDE. I use Qtcurve, but many people like Oxygen themes.Try installing the package 'oxygen-molecule', or even better download and install the Oxygen-GTK theme engine *.deb file found here: [http://kde-look.org/content/show.php/?content=136216](http://kde-look.org/content/show.php/?content=136216) Using either of these GTK theme engines will allow you to have the style of Oxygen, and they follow the colors you choose in KDE's color settings. Installing 'Qtcurve' is a nice way to have matching KDE and GTK applications too.

When you have installed a GTK theme engine for KDE, you can apply it by going to System Settings > Application Appearance > GTK+ Appearance > Widget Style: then pick the one you installed in the dropdown menu.

Also, some people create their own personas theme with "Personas Plus" [http://www.getpersonas.com/](http://www.getpersonas.com/) so they can have a matching theme.

Hope something I said here helps.

---

