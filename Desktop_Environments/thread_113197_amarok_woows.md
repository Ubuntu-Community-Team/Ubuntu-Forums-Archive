---
title: "amarok woows"
date: 2006-01-05
forum: Desktop Environments
---

### Post by zoglesby on 2006-01-05
I have been using GNOME for years and not to long ago some one told me about amaroK and I gave it a try, I liked it so much that I decided to run Kubuntu on my Ubuntu box, I ran sudo apt-get install kubuntu-desktop and then I booted in to KDE, to my suprise when I tried to start amaroK up I got and error and then it crashed, so I ran in from the command line to see what happend and this is what I got.

```
Camarok:     [PluginManager] Plugin trader constraint: [X-KDE-amaroK-framework-version] == 16 and [X-KDE-amaroK-plugintype] == 'engine' and [X-KDE-amaroK-name] != 'void-engine' and [X-KDE-amaroK-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-amaroK-framework-version] == 16 and [X-KDE-amaroK-plugintype] == 'engine' and [X-KDE-amaroK-name] == 'void-engine' and [X-KDE-amaroK-rank] > 0
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: ERROR creating database '/var/tmp/kdecache-zoglesby/ksycoca'!
kbuildsycoca: Wrong permissions on directory? Disk full?

```

I have looked around the forums and also installed from the SVN and I am still not getting it to work. Any ideas?

---

### Post by 23meg on 2006-01-05
Have you installed at least one of the xine, gstreamer and arts engines? They're available as separate packages.

---

### Post by zoglesby on 2006-01-06
Yes I have them all installed, and the only thing I have done to the computer was install the kubuntu-desktop

---

### Post by Lord Illidan on 2006-01-06
Try sudo amarok

---

### Post by snowjunkie on 2006-01-06
I done the same as yourself a while back and amarok works just fine for me.  No need to use sudo.  Have you tried a sudo apt-get update and upgrade?

---

### Post by zoglesby on 2006-01-06
I get the same problem with sudo amarok and I have updated and upgraded the system.

---

