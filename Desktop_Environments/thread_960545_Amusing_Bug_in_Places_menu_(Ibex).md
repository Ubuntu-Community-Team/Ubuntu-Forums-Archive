---
title: "Amusing Bug in Places menu (Ibex)"
date: 2008-10-27
forum: Desktop Environments
---

### Post by rpcutts on 2008-10-27
When I install SMPlayer on Ibex then try to click (in the places menu in the top panel) Home Folder, Desktop or any of my bookmarked folders then it launches SMPlayer (if there is an Ogg file in the home folder it will load it).

Removing SMPlayer puts behavior back to normal. 
Very strange, guess I'll just use VLC.

---

### Post by adlerhn on 2008-10-28
I have the same problem in my machine, but in my case Using any "place" from the Places menu opens the "SubDownloader" application instead.

Weird...

---

### Post by adlerhn on 2008-10-28
Ok, I have found the solution by a bit more googling:

[http://tennessee.ubuntuforums.com/showthread.php?p=6038154](http://tennessee.ubuntuforums.com/showthread.php?p=6038154)

> 1. Places menu not working correctly: vlc somehow hijacked "opening folders" task for itself. I simply changed "Open with" property for folder in nautilus.

So, the solution was, open Nautilus (like from Places -> Computer), then right click in any folder, properties, select the Open With tab, and from the list select Open Folder.

Easy :)

---

