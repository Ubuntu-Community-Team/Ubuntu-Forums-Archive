---
title: "I want gxine as default player for dvds"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Neo40 on 2005-10-30
Hi,

When I put a dvd,  how can I do to have gxine start instead totem?

Thanks for your help.

---

### Post by SickTwist on 2005-10-30
System -> Preferences -> Removable Drives and Media

1. Select the "Multimedia" tab
2. Ensure "Play Video DVD disks when inserted" is checked
3. Change the command to whatever you want (e.g. "gxine -S dvd:/" without quotes)

Another option:
Totem can use xine to play media instead of gstreamer. Just install the totem-xine package to do this:

sudo apt-get install totem-xine

The interface will look like totem but the movie will play like gxine.

---

