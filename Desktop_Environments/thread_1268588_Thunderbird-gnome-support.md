---
title: "Thunderbird-gnome-support"
date: 2009-09-17
forum: Desktop Environments
---

### Post by josegaert on 2009-09-17
Hellow!
This is my second post and yes, a second question. I have to get thunderbird to read my network-drives. Thunderbird doesn't seem to find them. I've read that it has something to do with the gnome-support for the network. So I've installed thunderbird-gnome-support but that, doesn't work either. I always have to work around it. Save my files to my desktop and then to network drive.
So, for some months now I don't know how I can solve it.
Do you guy's have any idea?
Thanks!

---

### Post by naaman on 2009-12-09
If you're using Karmic, thunderbird-gnome-support contains only 2 files under /usr/share/doc/thunderbird-gnome-support (ie. it's an empty package)..

Create a bookmark to the network share via Places -> Connect to Server.. and open the bookmark to trigger the gvfs mount.

Then press CTRL+H in the Attach File window to show the hidden folders in your home directory.  Open the .gvfs folder and open the folders underneath to get to the network drive files..

HTH.

---

