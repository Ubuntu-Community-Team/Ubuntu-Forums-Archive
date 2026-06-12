---
title: "Adding launchers for applications in KDE 4 panel"
date: 2009-01-12
forum: Desktop Environments
---

### Post by akwatve on 2009-01-12
Hi,

I recently upgraded to intrepid. Although it looks cool a lot of usability features are missing (or they are not so intuitive). How do I add launcher for a custom application into the panel. I want a launcher for my mixer (oss mixer).

In fact I would be nice if some one can guide me to a quick launch widget (if at all it exists).

Thanks

---

### Post by lykwydchykyn on 2009-01-12
There's a quick launcher coming in 4.2, but 4.1 doesn't have one built in; you can download one from kde-look.org ([http://www.kde-look.org/content/show.php/QuickLauncher+Applet?content=78061](http://www.kde-look.org/content/show.php/QuickLauncher+Applet?content=78061)), though it seems like I had a lot of trouble with that version.  It had a bug saving settings, and seems like it took some post-install tinkering to get it to work.

---

### Post by akwatve on 2009-01-12
I did see that but it is not available for x86_64

---

### Post by akwatve on 2009-01-12
Just an update:

I tried to build the package from the sources but it gave an ominous looking error :

> /home/foo/plasma-applet-quicklauncher-0.5/src/quicklauncher.cpp:26:35: error: kworkspace/kworkspace.h: No such file or directory   
make[2]: *** [CMakeFiles/plasma_applet_quicklauncher.dir/quicklauncher.o] Error 1
make[1]: *** [CMakeFiles/plasma_applet_quicklauncher.dir/all] Error 2
make: *** [all] Error 2
[ 25%] Building CXX object CMakeFiles/plasma_applet_quicklauncher.dir/quicklauncher.o

home/foo/plasma-applet-quicklauncher-0.5/src/quicklauncher.cpp:26:35: error: kworkspace/kworkspace.h: No such file or directory
make[2]: *** [CMakeFiles/plasma_applet_quicklauncher.dir/quicklauncher.o] Error 1
make[1]: *** [CMakeFiles/plasma_applet_quicklauncher.dir/all] Error 2
make: *** [all] Error 2


---

### Post by lykwydchykyn on 2009-01-12
You're missing some build dependencies; I think you need kdebase-workspace-dev installed.

---

### Post by akwatve on 2009-01-12
Ok


I finally compiled and installed it. But it does not appear in the list of widgets. I believe I need to "add" it explicitly. But where should I look for the file ?

This may be a bit dumb but I have never done this before

Thanks again

---

### Post by lykwydchykyn on 2009-01-13
> **akwatve said:**
> Ok


I finally compiled and installed it. But it does not appear in the list of widgets. I believe I need to "add" it explicitly. But where should I look for the file ?

This may be a bit dumb but I have never done this before

Thanks again

No, it's not your fault; I think the package puts the files in the wrong place, as I noticed some of them do.  So even though you compiled it correctly, it ends up in the wrong place.  

I've upgraded my system to the 4.2 release candidate, so I'm going purely on my poor memory here, but I think the install puts the files under /usr/lib/kde4/, and you want it just under /usr.  There are two files, one is a library (ends in .so) and the other is a .desktop file that creates the menu entry.  The .so needs to be in /usr/lib/kde4 and the .desktop in /usr/share/kde4/services.

Keep in mind, kde 4.2 has this built in, and it should be released in two weeks, give or take.  There will most certainly be packages for Intrepid.  So if this is too much to take I'd wait a few weeks then upgrade.

---

### Post by akwatve on 2009-01-14
Hmm
Your suggestion makes a lot of sense. I will give this a last try today. If it works ... fine.. else I will rather wait for kde4.2

---

### Post by 3rdalbum on 2009-01-14
I ended off doing a combination of three things:

1. Adding the programs to the "Favourites" in the KDE menu
2. Added a Folder View plasmoid to the bottom of my desktop, opened to ~/Launchers/. This folder contains launchers to some of my favourite programs.
3. Pressing Alt-F2 and typing the name of the program I want to use.

---

### Post by akwatve on 2009-01-14
That may be a good work around...

Anyways, I finally got it up and running.
Just for the purpose of documentation:

1) The .desktop file plasma-applet-quicklauncher.desktop was in  /share/kde4/services/ folder
2) I had to manually move it to /usr/share/kde4/services/

Now my I can see the widget in the list of available widgets

Thanks all for the help

---

