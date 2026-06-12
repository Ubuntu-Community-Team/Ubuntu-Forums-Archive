---
title: "VLC takes over gnome directory viewer"
date: 2011-11-19
forum: Desktop Environments
---

### Post by csmilovitz on 2011-11-19
I just upgraded to 11.10.  I dislike the Unity frontend and still use Gnome.  

The new Ubuntu seemed to be working fine.  Then I used Synaptic to install vlc, a video player which I was using before in 11.04.  After installing vlc, whenever I opened a directory with the Gnome graphic interface (eg Places/<disk name>), instead of having the directory open as you would expect, it opens in the select screen for vlc.  When you choose a file, vlc tries to open it as a media file and play it, which almost always results in an error.  I'm just browsing my directories, and most of them don't contain media files.

If I remove (ie uninstall) vlc, everything is fine.  Reinstalling vlc brings the problem back.  The problem occurs even if I do an "uninstall completely" before reinstalling.

This seems totally weird.

Craig

---

### Post by mc4man on 2011-11-20
open this file
```
gedit ~/.local/share/applications/mimeapps.list
```

In the **[Default Applications]** section there will be a line

inode/directory=nautilus-folder-handler.desktop

Remove the line completely & save

(an upcoming update to nautilus would have fixed this for you but it's still in oneiric-proposed
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788)

---

### Post by csmilovitz on 2011-11-20
Thanks.  I followed your directions and they worked.  Hope this fix makes it into the release soon.

Craig

---

