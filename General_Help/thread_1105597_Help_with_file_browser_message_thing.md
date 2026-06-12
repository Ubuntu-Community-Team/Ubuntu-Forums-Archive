---
title: "Help with file browser message thing"
date: 2009-03-24
forum: General Help
---

### Post by Syrinx Priest on 2009-03-24
Hi, My first post. I have been using Ubuntu for about 2 months and I love it. There is just one tiny thing that irritates me a little bit. It's a type of message that won't go away in the File Browser (mainly my WD hdd). It says: "The media contains software." "These files are on a Picture CD.". I have attached a screencap. If anyone can help, please throw something in.

---

### Post by Tim Sharitt on 2009-03-25
Open gconf editor by hitting Alt-F2 (or opening a terminal) and enter ```
gconf-editor
```
Got to / > apps > nautilus > preferences and check the box beside media_autorun_never

---

### Post by Syrinx Priest on 2009-03-25
Sorry, that didn't work. I don't mind the autorun, I just don't want that message box with those 2 messages. If there is no way to do that; I can live with it, just thought to clear up some space(area) it uses up when I want to browse my things. Thanks

---

### Post by aquasync on 2009-09-19
I know this is a bit late, but I was having the same problem and its a bit annoying. By default theres a check for a PICTURES folder (note all caps), which triggers recognition as a "Picture CD", regardless of whether the device is a CD or not :/. What makes this worse, is that on a case-insensitive file system (eg FAT), having a top-level Pictures folder is not very uncommon.

I hacked around this by commenting out the relevant section is /usr/share/mime/packages/freedesktop.org.xml (where it defines the mimetype x-content/image-picturecd). You can probably use the same approach to avoid other unwanted bars coming up in nautilus.

---

