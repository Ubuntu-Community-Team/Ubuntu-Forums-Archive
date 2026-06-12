---
title: "Gscreendump v0.2 has been released."
date: 2009-03-15
forum: General Help
---

### Post by moma on 2009-03-15
Hello everybody,

**The amazing Gscreendump version 0.2 has now been released.** Gscreendump is mainly a screenshot-taking utility but it can also manipulate images via ImageMagick commands. 

It can take screenshots of anything.
[[img]http://bildr.no/thumb/367363.jpeg[/img]](http://bildr.no/view/367363)

Gscreendump's "multiple selection" feature lets you run the same command on any number of images.

Gscreendump has of course a built-in revision system so you can any time roll back changes you did on your holiday pictures || screenshots. Just clik the "Undo" button or select "Undo all selected images" from the menu.

[[img]http://bildr.no/thumb/367281.jpeg[/img]](http://bildr.no/view/367281)

And you can easily add and test your own image-manipulation commands on it.

[[img]http://bildr.no/thumb/367277.jpeg[/img]](http://bildr.no/view/367277)

**Installation on Ubuntu:**
1) Install pre-requirements/dependencies.
$ [COLOR="DarkGreen"]sudo aptitude install libmagick10 imagemagick libgtkimageview0 gnome-web-photo[/COLOR]

2) Download suitable (32 -or 64bits) Ubuntu-package from [http://code.google.com/p/gscreendump/downloads/list](http://code.google.com/p/gscreendump/downloads/list)

Install the package by clicking on it, or download it to your home-folder and type:
$ [COLOR="DarkGreen"]sudo dpkg -i gscreendump_0.2_*.deb[/COLOR]

If your system complains about missing dependencies, run:
$ [COLOR="DarkGreen"]sudo aptitude install -f[/COLOR]
------------------

EDIT: It should now install a menu entry under Applications -> Accessories (or Graphics) menu. If not, start it form command line by typing:
$ [COLOR="DarkOliveGreen"]gscreendump[/COLOR]

------------------
**Development and installation from source code:**
Download source code from [http://code.google.com/p/gscreendump/]("http://code.google.com/p/gscreendump/"), then read the [INSTALL]("http://code.google.com/p/gscreendump/source/browse/trunk/INSTALL") and [README]("http://code.google.com/p/gscreendump/source/browse/trunk/README") files (in the source's gscreendump* directory) for further instructions.

The wiki-page ([http://code.google.com/p/gscreendump/w/list]("http://code.google.com/p/gscreendump/w/list")) has more information about the installation.
------------------

The concept of Gscreendump is ready. In the next release I will only fix bugs and make sure all strings are translatable. **I do also search for other developers whoo are willing to contribute and possibly take over the further development of Gscreendump. ** So take contact and send a message to: osmoma (at) gmail (dot) com. I am sitting and waiting.

Good luck :P

EDIT: Special thanks to Fred Weinhaus for his excellent [IM scripts...]("http://www.fmwconcepts.com/imagemagick")

Most kindly 
 Moma (Osmo Antero Maatta) from Grønland/Oslo, Norway.
---------------

[COLOR="Red"]EDIT 20.mars.2009:[/COLOR] One important fix in the code.
Screenshots now include correct mouse pointer or cursor (for the application you take a screenshot of). You can also add effects to the mouse pointer.

The screenshot dialog has now these options.
[[img]http://bildr.no/thumb/370572.jpeg[/img]](http://bildr.no/view/370572)

Sample effects (zoom the pointer/cursor or draw a circle around its location).
[[img]http://bildr.no/thumb/370567.jpeg[/img]](http://bildr.no/view/370567)

---

### Post by lovinglinux on 2009-03-15
When I try to run the application I get these errors:

```
** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/thumbnails/list_width.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/thumbnails/list_height.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/plugins/list_width.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/screenshot_counter.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/toolbars/standard/show.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/toolbars/style.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/last_opened_file.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/last_import_path.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/last_save_as_file.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/main_window/x.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/main_window/y.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/main_window/width.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/main_window/height.


** (gscreendump:31248): WARNING **: sd_gconf.c: Failed to get list for key /apps/gscreendump/folder_list.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/last_opened_folder.


** (gscreendump:31248): WARNING **: sd_conf.c: Cannot find key /apps/gscreendump/start_with_defaults.

gscreendump: symbol lookup error: gscreendump: undefined symbol: gtk_image_new_from_gicon

```

How do I fix this?

---

### Post by moma on 2009-03-15
Hello,
Thanks for trying Gscreendump.

Those [COLOR="SlateGray"]"WARNING **: sd_conf.c: Cannot find key..."[/COLOR] messages are harmless. When you run the program first time, there will not be entry for Gscreendump in the Gnome's configuration database. Those messages will disappear when you run the program couple of times. ((start gconf-editor, and browse to "apps" -> "gscreendump" if you want to see the configuration values)).

The second kind of message is much more severe.[COLOR="SlateGray"]"gscreendump: symbol lookup error: gscreendump: undefined symbol: gtk_image_new_from_gicon"[/COLOR]. It will propably make Gscreendump crash.  Does it crash in your case?

What is your Ubuntu version (is it Ubuntu 8.10.- Is it 32bits, 64bits)?

Do you have any data in /usr/share/gscreendump? 
Type 
$ [COLOR="SeaGreen"]ls -lR  /usr/share/gscreendump[/COLOR]

And compare the output (roughly) to the attached file "gscreendump_listing1.txt"  
Du you have any icons in the /usr/share/gscreendump/pixmaps/ directory?

Would you take the effort to compile Gscreendump from source and hunt down the bug? (TIA) ;-)
---------

EDIT: In my first message I suggested that Gscreendump would also install on Jaunty Jackalope (from the same .deb package). However, I just discovered that at least one important library is different in Ubuntu 8.10 and 9.04 (alpha). The libray is libmagickwand1.  Source code itself does not need any changes, but the source must be configured (./configure) and compiled (make) on each Ubuntu version.

So Jaunty Jackalope will require its own .deb file which I'll prepare when Jaunty is released in april.

---

### Post by lovinglinux on 2009-03-15
> **moma said:**
> What is your Ubuntu version (is it Ubuntu 8.10.- Is it 32bits, 64bits)?

Would you take the effort to compile Gscreendump from source and hunt down the bug? (TIA) ;-)

Thanks for the support.

I'm running Hardy 32 bits

Unfortunately, I still don't know how to compile.

---

### Post by moma on 2009-03-15
Re-hello,

I edited my previous message. Would you re-read it. Particularly I asked if you have any data in /usr/share/gscreendump ?

Can you re-install the entire app by typing (one line at a time) 
```
sudo aptitude install libmagick10 imagemagick libgtkimageview0 gnome-web-photo
```
This is for 32bits Ubuntu:
```
wget http://gscreendump.googlecode.com/files/gscreendump_0.2_i386.deb
```
```
sudo dpkg -i gscreendump_0.2_i386.deb
```
--------------
To the the missing "gtk_image_new_from_gicon" function. It is part of the ordinary gtk2 library. I studied

$ [COLOR="SeaGreen"]grep -R gtk_image_new_from_gicon /usr/include [/COLOR]
/usr/include/gtk-2.0/gtk/gtkimage.h:GtkWidget*gtk_image_new_from_gicon

Then, what package contains gtkimage.h?
$ [COLOR="SeaGreen"]dpkg -S /usr/include/gtk-2.0/gtk/gtkimage.h[/COLOR]
libgtk2.0-dev: /usr/include/gtk-2.0/gtk/gtkimage.h

AFAIK, libgtk2.0 is very basic stuff in any GNOME installation. Do you miss "libgtk2.0-0" package?

---

### Post by worksofcraft on 2010-03-03
There is no 32 bit download :(

> sudo aptitude install libmagick10 imagemagick libgtkimageview0 gnome-web-photo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "libmagick10"

...

so I tried building from sources

...
> configure: error: Cannot find ImageMagick library Wand. Install libmagick9-dev (or later) package.
> sudo apt-get install libmagick9-devReading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libmagickwand-dev instead of libmagick9-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmagickwand-dev: Depends: libmagickwand1 (= 7:6.4.5.4.dfsg1-1ubuntu3) but 7:6.4.5.4.dfsg1-1ubuntu3.1 is to be installed
                     Depends: libmagickcore-dev (= 7:6.4.5.4.dfsg1-1ubuntu3) but it is not going to be installed
E: Broken packages


Can anyone help, how do I cope with the dependencies on superseded packages please?

---

