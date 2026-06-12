---
title: "&quot;Open Containing Folder&quot; always opens evince, much to my frustration"
date: 2011-07-07
forum: Desktop Environments
---

### Post by reallyasi9 on 2011-07-07
I have a problem that has been plaguing me for several months now.  Every time I select the option to open a containing folder in any context, evince opens and displays an error message telling me it cannot open a file of that type.

The "open a containing folder" I am speaking of is any such action in any application.  The most prominent examples are Chromium and Firefox, when I select the option after downloading a file.  Other examples include Banshee, when you right-click on a song and request to view the song in its folder, or when I attempt to view the extracted files in File Roller after performing an extraction.

This problem is present under Metacity, Gnome Shell, and Unity, but not Plasma, which leads me to believe it is a problem with Gnome's settings.  I have looked through the Preferred Applications settings in Gnome and cannot find a "directory" or "folder" MIME type to which I can assign an application.  Can anybody help?

---

### Post by computermacgyver on 2011-12-07
See the final response on this bug:
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/864992](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/864992)
for a work around for Nautilus. You may also want to check that your preferred application for filebrowser is set correctly. Run exo-preferred-applications in the terminal.

---

### Post by steronius on 2012-07-12
(for firefox downloads issue with open containing folder)

solved:
firefox>preferences>content>
content type: file
action: \usr\bin\exo-open

(or xdg-open, or gnome-open)

---

