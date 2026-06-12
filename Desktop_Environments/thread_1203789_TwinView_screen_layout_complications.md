---
title: "TwinView screen layout complications"
date: 2009-07-03
forum: Desktop Environments
---

### Post by anescient on 2009-07-03
I'm having a problem altering my dual display setup, with one nVidia card, using nVidia's driver.

I used to have a 1024x768 display on the right side of my 1920x1200, set it up with nvidia-settings. Always worked great. I even changed the offset/position of the smaller display with no trouble.

I removed the smaller display for a while, and now I'm trying to set up a 1280x1024 in its place. The problem is that something, somewhere, refuses to change the layout of my screen. Unless I set up the second display with the exact same resolution and offset as the old one, I get areas of screen where nothing is drawn except the mouse cursor. No matter what configuration I use, only the old 1920x1200 with a 1024x768 area on the side is drawn.

nvidia-settings -is- writing xorg.conf correctly, and the displays -are- set up with the positions and resolutions I specify, but any area outside of the old layout is useless. Black. Only the cursor will appear there.

I tried removing the nvidia driver, then using System->Preferences->Display to set everything up, and it works perfectly. When I re-enable the nvidia driver, it's back to braindead and broken again.

I'm really not sure what it is that's remembering and clinging to that old screen layout. Maybe I need to more thoroughly remove the nvidia driver, but I don't know how.

---

