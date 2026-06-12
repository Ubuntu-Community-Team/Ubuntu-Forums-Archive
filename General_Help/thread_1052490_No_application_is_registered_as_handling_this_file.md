---
title: "No application is registered as handling this file"
date: 2009-01-27
forum: General Help
---

### Post by woknam66 on 2009-01-27
It used to be that every time that I clicked on Places (along the top bar), it gave me many folders I could open. Now (one reboot later), I only have "Home Folder", "Desktop", "Documents", "Music", "Pictures", and "Videos", but whenever I clock on one of them, it says "No application is registered as handling this file." How do I fix this?

P.S. I am new to Ubuntu.

---

### Post by mikewhatever on 2009-01-27
alt+f2, type in 'nautilus' without quotes, right click on any folder, select Properties and go to the 'Open with' tab. Select 'Open folder' instead of another application.

---

### Post by woknam66 on 2009-01-27
When I type "nautilus", should it automatically change it to "nautilus-sendto"? When I force it to just use "nautilus", it comes up with "Error stating file '/home/woknam66/nautilus': No such file or directory". When I use "nautilus-sendto", should anything visible happen? Also, all of the folders on the desktop are gone, so I have nothing left to right-click on, and whenever I try to right-click on something in the "Places" menu, it just comes up with an error message saying "No application is registered as handling this file" instead of giving me a menu.

---

### Post by mikewhatever on 2009-01-28
> **woknam66 said:**
> When I type "nautilus", should it automatically change it to "nautilus-sendto"? When I force it to just use "nautilus", it comes up with "Error stating file '/home/woknam66/nautilus': No such file or directory". When I use "nautilus-sendto", should anything visible happen? Also, all of the folders on the desktop are gone, so I have nothing left to right-click on, and whenever I try to right-click on something in the "Places" menu, it just comes up with an error message saying "No application is registered as handling this file" instead of giving me a menu.

No, if you type 'nautilus' and get an autocomplete option of 'nautilus-sendto' there is a problem, because the system doesn't know what nautilus is. Did you replace the file manager with something else? What are the outputs of the following:
dpkg -s nautilus
which nautilus

---

### Post by woknam66 on 2009-01-28
I assume those should go into terminal as two seperate, sequential commands, right?

---

### Post by woknam66 on 2009-01-29
Hello? Anyone?

---

### Post by gettinoriginal on 2009-01-29
yes, they should. Then post the output  :p

---

### Post by woknam66 on 2009-01-30
Okay, when I first start my computer, instead of just giving me the choice between Windows XP and Ubuntu, it gives me three choices. I gives me XP, and then two choices of Ubuntu. The first one is "Ubuntu 8.10, kernel 2.6.27-9-generic", and the second one is "Ubuntu 8.10, kernel 2.6.27-7-generic". First I booted into "Ubuntu 8.10, kernel 2.6.27-9-generic".

After I typed in "dpkg -s nautilus", it gave me:
```
Package: nautilus
Status: deinstall ok config-files
Priority: optional
Section: gnome
Installed-Size: 2360
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Version: 1:2.24.1-0ubuntu1
Config-Version: 1:2.24.1-0ubuntu1
Replaces: libnautilus2-2
Provides: nautilus-extensions-2.0
Depends: libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libeel2-2 (>= 2.24.0), libexempi3, libexif12, libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.18.0), libgnome-desktop-2-7 (>= 1:2.23.90), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgtk2.0-0 (>= 2.14.1), liblaunchpad-integration1 (>= 0.1.17), libnautilus-extension1 (>= 1:2.22.2), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.21.6), librsvg2-2 (>= 2.18.1), libselinux1 (>= 2.0.59), libstartup-notification0 (>= 0.8-1), libx11-6, libxml2 (>= 2.6.27), nautilus-data (>= 1:2.24), nautilus-data (<< 1:2.25), shared-mime-info, gnome-control-center (>= 2.6), desktop-file-utils (>= 0.7), gvfs-backends
Recommends: eject, nautilus-cd-burner (>= 2.6), librsvg2-common, xdg-user-dirs, gnome-app-install
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, gamin | fam
Conflicts: libnautilus2-2, libnautilus2-dev
Description: file manager and graphical shell for GNOME
 Nautilus is the official file manager for the GNOME desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the GNOME
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.
Homepage: http://www.gnome.org/projects/nautilus/
Original-Maintainer: Josselin Mouette <joss@debian.org>

```

And after I typed in "which nautilus", it gave me nothing.

---

### Post by woknam66 on 2009-01-30
Now I'm in "Ubuntu 8.10, kernel 2.6.27-7-generic".

After I typed in "dpkg -s nautilus", it gave me:

```
Package: nautilus
Status: deinstall ok config-files
Priority: optional
Section: gnome
Installed-Size: 2360
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Version: 1:2.24.1-0ubuntu1
Config-Version: 1:2.24.1-0ubuntu1
Replaces: libnautilus2-2
Provides: nautilus-extensions-2.0
Depends: libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libeel2-2 (>= 2.24.0), libexempi3, libexif12, libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.18.0), libgnome-desktop-2-7 (>= 1:2.23.90), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgtk2.0-0 (>= 2.14.1), liblaunchpad-integration1 (>= 0.1.17), libnautilus-extension1 (>= 1:2.22.2), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.21.6), librsvg2-2 (>= 2.18.1), libselinux1 (>= 2.0.59), libstartup-notification0 (>= 0.8-1), libx11-6, libxml2 (>= 2.6.27), nautilus-data (>= 1:2.24), nautilus-data (<< 1:2.25), shared-mime-info, gnome-control-center (>= 2.6), desktop-file-utils (>= 0.7), gvfs-backends
Recommends: eject, nautilus-cd-burner (>= 2.6), librsvg2-common, xdg-user-dirs, gnome-app-install
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, gamin | fam
Conflicts: libnautilus2-2, libnautilus2-dev
Description: file manager and graphical shell for GNOME
 Nautilus is the official file manager for the GNOME desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the GNOME
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.
Homepage: http://www.gnome.org/projects/nautilus/
Original-Maintainer: Josselin Mouette <joss@debian.org>
```

And after I typed in "which nautilus", it gave me nothing again.

---

### Post by gettinoriginal on 2009-01-30
The two ubuntu choices are just kernel header updates, security/bug fixes.  I always keep 2, as if the latest crashes, I can boot into the older one.

Type into terminal:
```
nautilus
```

If that does not let you into your file browser, then do this:

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by woknam66 on 2009-01-30
After I typed in "nautilus", it told me that nautilus was not installer, and gave me instructions on how to install it. I followed those instructions, a quick reboot, and it worked! I only have two questions left now, why do I have two options to boot into Ubuntu and how do I fix it? And how do I get my wifi to work?

P.S. I already have the wifi driver installed.

---

### Post by Roanoke on 2009-04-10
Kernel stuff:
sudo apt-get install startupmanager
Wifi: No idea.

---

### Post by wallybescotty on 2010-04-22
if you cant get your places to work in the main menu panel, this is what i did to fix it, alt f2 type
nautilus, and then right click the folder and go to open with application
and click the triangle where it says use custom command and paste nautilus

then click ok or hit enter, and it should fix it. i was having the same problem.

---

