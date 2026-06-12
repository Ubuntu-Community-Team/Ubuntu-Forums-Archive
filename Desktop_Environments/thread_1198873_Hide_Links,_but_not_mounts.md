---
title: "Hide Links, but not mounts"
date: 2009-06-28
forum: Desktop Environments
---

### Post by madfitz on 2009-06-28
I was looking for a way to cleanup my desktop. I hate having a multitude of links on my desktop, but I like to have mounted drives listed there for easy access.

My setup. I have a linux server where all my actual personal data exists. I mount this on a drive for my primary user (only one account on this system). I had wanted to mount the entire user's directory to the server, but this proved problematic (especially if there were issues with the network, or the server was off line). So I simply mount to a directory in "/home/{user}/ServerMount/" and link the common directories to the representative directories on the server.
i.e. Desktop, Documents, Video, Music, Pictures, etc.

However this results in my desktop being cluttered, not only with the ServerMount (which I want) but also all those links (which I don't want).

I found this script which works splendidly, but it removes everything from the desktop.

[http://bayu.freelancer.web.id/2009/05/03/showhide-desktop-icon-on-ubuntu/]("http://bayu.freelancer.web.id/2009/05/03/showhide-desktop-icon-on-ubuntu/")

So is there a way in which to hide only links, but show any and all mounted drives (i.e. usb/thumbdrives/ServerMount, etc)?

Thanks

---

