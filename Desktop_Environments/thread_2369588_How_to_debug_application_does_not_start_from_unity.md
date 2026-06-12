---
title: "How to debug application does not start from unity launcher"
date: 2017-08-24
forum: Desktop Environments
---

### Post by 7-webmaster on 2017-08-24
Installing an application created an icon in the Unity launcher.  When I click on that icon it flickers for a few seconds but the application is not launched.  How to I find out what went wrong?

The same thing happens if I search for the application and try to launch it that way.

If i go to the terminal and type ocrfeeder, the application I am trying to launch, I get:

```
/usr/lib/python2.7/dist-packages/ocrfeeder/util/lib.py:26: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python2.7/dist-packages/ocrfeeder/studio/widgetPresenter.py:31: PyGIWarning: GooCanvas was imported without specifying a version first. Use gi.require_version('GooCanvas', '2.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GooCanvas, Gdk, GObject, GLib, GdkPixbuf, GtkSpell
/usr/lib/python2.7/dist-packages/ocrfeeder/studio/widgetPresenter.py:31: PyGIWarning: GtkSpell was imported without specifying a version first. Use gi.require_version('GtkSpell', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GooCanvas, Gdk, GObject, GLib, GdkPixbuf, GtkSpell

```

and the application starts.

---

### Post by wheatpenny2 on 2017-08-24
I'm very much interested in the answer to this as that has happened to me with 2 or three apps.

---

### Post by again? on 2017-08-24
If you look at it's launcher @ /usr/share/applications/ocrfeeder.desktop you'll see the Exec command is
```
ocrfeeder -i %f
```

According to "man ocrfeeder" the -i option requires an image argument.
> -i IMAGE1 [IMAGE2 ...], --images=IMAGE1 [IMAGE2 ...]
Add the specified images to OCRFeeder after opening it

...and you'll see using "ocrfeeder -i" with no argument fails.
```
**glen@GU17:~$ ocrfeeder -i**
/usr/lib/python2.7/dist-packages/ocrfeeder/util/lib.py:26: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python2.7/dist-packages/ocrfeeder/studio/widgetPresenter.py:31: PyGIWarning: GooCanvas was imported without specifying a version first. Use gi.require_version('GooCanvas', '2.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GooCanvas, Gdk, GObject, GLib, GdkPixbuf, GtkSpell
/usr/lib/python2.7/dist-packages/ocrfeeder/studio/widgetPresenter.py:31: PyGIWarning: GtkSpell was imported without specifying a version first. Use gi.require_version('GtkSpell', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GooCanvas, Gdk, GObject, GLib, GdkPixbuf, GtkSpell
Gtk-Message: Failed to load module "unity-gtk-module"
Usage: ocrfeeder [options]

[COLOR="#FF0000"]ocrfeeder: error: -i option requires an argument[/COLOR]
``` 

In unity (doesn't work in gnome-shell) you can drag and drop an image from the file browser onto the launcher icon and ocrfeeder will open displaying that image.
Don't know how ocrfeeder is used by you but if you prefer just a normal launcher you can remove the -i option from 
the Exec command.

Best way to do this is to copy the system .desktop file to your user local directory and edit.(doesn't get overwritten if application is updated)
Launchers in ~/.local/share/applications will override the same named launcher in /usr/share/applications
```
cp /usr/share/applications/ocrfeeder.desktop ~/.local/share/applications

```

Open and edit copied launcher 
```
gedit ~/.local/share/applications/ocrfeeder.desktop
```

Change the line 
```
Exec=ocrfeeder -i %f
```
to
```
Exec=ocrfeeder
```
You may have to log out and back in to take effect.

If you want to revert back to default behaviour just remove the edited launcher.
```
rm ~/.local/share/applications/ocrfeeder.desktop
```

---

### Post by 7-webmaster on 2017-08-26
Thank you for going above and beyond to identify the problem and explaining how to solve it.

---

### Post by mc4man on 2017-08-26
Wierd thing about that .desktop
(- the %f just allows the app to show in the context menu, could have been %F, %u or %U 

A bug was filed over a year ago & forwarded  upstream

It used to be Exec=ocrfeeder,  the attempt to make it work from context menu was in a patch - 
> --- ocrfeeder.orig/resources/ocrfeeder.desktop.in
+++ ocrfeeder/resources/ocrfeeder.desktop.in
@@ -4,7 +4,7 @@ Type=Application
 _Name=OCRFeeder
 _Comment=The complete OCR suite.
 TryExec=ocrfeeder
-Exec=ocrfeeder
+Exec=ocrfeeder -i %f
 Icon=/usr/share/ocrfeeder/icons/ocrfeeder.svg
 MimeType=image/bmp;image/gif;image/jpeg;image/jpg;image/pjpeg;image/png;image/tiff;
 Categories=Application;Office;


[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=827196](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=827196)

To use from the context menu or DnD  it would need the -i, to open just the app then no -i
Probably should of come with 2 .desktops, noted in the upstream report but no action ever taken
[https://bugzilla.gnome.org/show_bug.cgi?id=767732](https://bugzilla.gnome.org/show_bug.cgi?id=767732)

Edit: pretty easy to set up with 2 .desktops, that way you can open the app (no input file) or open the app from context menu.

---

### Post by 7-webmaster on 2017-09-02
> **mc4man said:**
> 

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=827196](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=827196)

To use from the context menu or DnD  it would need the -i, to open just the app then no -i
Probably should of come with 2 .desktops, noted in the upstream report but no action ever taken
[https://bugzilla.gnome.org/show_bug.cgi?id=767732](https://bugzilla.gnome.org/show_bug.cgi?id=767732)

Edit: pretty easy to set up with 2 .desktops, that way you can open the app (no input file) or open the app from context menu.

I feel the issue is that ocrfeeder demands that input image files be identified by the -i parameter.  Most programs take any argument that is **not** preceded by an argument name as a file name to be processed.  But ocrfeeder demands that input file names be preceded by --images or -i for short.  For example libreoffice (soffice --help), which appears in almost everyone's menu bar, says:

"Remaining arguments will be treated as filenames or URLs of documents to open."

---

### Post by mc4man on 2017-09-02
> **7-webmaster said:**
> I feel the issue is that ocrfeeder demands that input image files be identified by the -i parameter."
Not at all. The current .desktop is only useful when opening ocrfeeder on a file, i.e. thru the context menu or a set file association. 
That would seem to be the way it would generally be used. 

For unity dock or any other dock that supports desktop actions I'd set up the .desktop like this (basic, not showing name/comment translations..

```
[Desktop Entry]
Version=1.0
Type=Application
Name=OCRFeeder
Comment=The complete OCR suite.
TryExec=ocrfeeder
Exec=ocrfeeder -i %f
NoDisplay=true
Icon=/usr/share/ocrfeeder/icons/ocrfeeder.svg
MimeType=image/bmp;image/gif;image/jpeg;image/jpg;image/pjpeg;image/png;image/tiff;
Actions=app;

[Desktop Action app]
Name=Open OCRFeeder
Exec=ocrfeeder
OnlyShowIn=Unity;Gnome;


```
This would allow thru the single .desktop,
1. Available & working thru context menu or set file  association
2. DnD of a file on the dock icon
3. A r. click on icon > Open OCRFeeder will open it with no file loaded

---

