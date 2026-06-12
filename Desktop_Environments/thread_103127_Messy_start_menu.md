---
title: "Messy start menu"
date: 2005-12-13
forum: Desktop Environments
---

### Post by gt24 on 2005-12-13
I installed KDE a while ago and later uninstalled it.  The issue with KDE is that, by default, the "start menu" has a TON of stuff in it!!  I can understand KDE populating the start menu with Gnome applications and alike... but it also populates all the Gnome control panel widgets and... well... all the Gnome EVERYTHING.  In reverse, Gnome only adds a few icons to its' start menu, so it is more bearable.

Any advice on how to live with KDE if I do install it in the future, other than manually removing every start menu entry one by one hoping that I won't need it in this window manager?

---

### Post by kairu0 on 2005-12-14
The only way to get rid of the extra entries would be delete the programs behind them (Synaptic/Adept) or remove only the shortcuts from the K menu.

Gnome AIMS to be simple ("it just works"); KDE has a slightly different philosophy. That's why the KDE menu is more thorough.

---

### Post by Footer on 2005-12-28
[QUOTE=kairu0]The only way to get rid of the extra entries would be delete the programs behind them (Synaptic/Adept) or remove only the shortcuts from the K menu.

Gnome AIMS to be simple ("it just works"); KDE has a slightly different philosophy. That's why the KDE menu is more thorough.[/QUOTE]

Chiming in a bit late here...But...is this really, really true...?  I've been using U/Kubuntu for about 6 months now and although I like the 'clean' start you get with Ubunutu (minimal apps on the start menu), I prefer KDE.  So am I really stuck with all those programs that get installed with Kubuntu or is the only way to clean up that start menu, doing it the old fashioned way (one by one or removing shortcuts) as stated above?

Say it isn't so!  I like to USE my machine which is why I haven't taken the time to clean up the start menu but it sure makes programs hard to find sometimes.  Perhaps there's a 'feature' like in Windows where the programs that you haven't used in while auto-hide?  If so, I haven't figured out how to enable it.

:)

---

### Post by jamboarder on 2005-12-29
If you want cleanup the menus in KDE or GNOME a bit, go to /usr/share/applications.  All the menu entries reside here.  

Open the .desktop file in a text editor (using sudo) for each app you don't want to show up only in GNOME, not in KDE, and append "OnlyShowIn=GNOME" to the end of the file.  Similarly if you only want it to show up in KDE, not GNOME, then append "OnlyShowIn=KDE".

Most of the KDE applications are in the "kde" folder under /usr/share/applications.

A quick way to do all the .desktop files in a folder is creating a bash script with the following line (change KDE to GNOME depending on which menu you would like to clean up):
  
  for i in *.desktop; do echo "OnlyShowIn=KDE" >> $i; done

So you can create a temporary folder and move all the .desktop files you want to change there, run the script (using sudo) in that folder then move them back.  Otherwise just edit the .desktop files one at a time (it's worth it to have the cleaned up menus).

I did this to get exactly the applications I wanted in my KDE menu (all the KDE stuff with a smattering of other apps like GIMP, OpenOffice and Firefox) and in my GNOME menu (all the GNOME/GTK+ stuff plus Amarok, k3b).

KDE and GNOME use the same menu system so one should be no more inherently complex than the other.  A clean install of kubuntu will have a KDE menu structure mostly similar to GNOME in simplicity, only it's populated with KDE apps instead.  An install of kubuntu-desktop on top of ubuntu will have all or most of the GNOME and KDE apps throughout the menu structure because that's what's installed.  The .desktop file format provides a way to keep the menu items for each desktop clean and seperate.  As of yet though the menu editors in GNOME and KDE don't provide a way to change this setting via a GUI, hence the method described above.

Hope this helps.

---

### Post by Footer on 2005-12-29
Hey!  Thanks for the detailed instructions on how to do this.  I think this is almost exactly what the Dr. ordered.  I do like to keep both GNOME and KDE around and I would like a nice, tidy menu of each.  However, I think I need a third option.

If I don't want the app. in either, but I want to keep the app. installed, could I just add:  "OnlyShowIn=" (ie. leave it blank)?  Would that take it out of both menus?  Then again, if I'm never going to use the app, perhaps it makes sense to just remove it and be done with it ... ?

Thanks so much for your reply.  I think I'm really close to getting a tidy start menu ... FINALLY!

:)

---

