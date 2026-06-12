---
title: "MP3 Sharing from Ubuntu to VirtualBox WinXP"
date: 2009-03-03
forum: General Help
---

### Post by Black Razor on 2009-03-03
OK,

So I've decided I can't keep away from making mix CD's for my friend any longer, and so I need to head back to my old trusty friend Mixmeister.  Now, I am pretty much a mid-level experience VirtualBox user, and familiar with linking XP and Ubuntu using REAL computers, but I don't know how to make a network from my Ubuntu directory containing my MP3 files to my VirtualBox WinXP machine.  Ideally I want not to have to create a FAT partition, because my HD is set up in a mirrored config, and I dont want to screw with those settings.  Any takers?

---

### Post by davmac on 2009-03-09
I've just had a go myself now and it was as easy as right clicking on the directory on the host system and choosing to share. This will offer to install Samba if you don't already have it.

Then go to the WinXP guest, browse the network, as you would on a standalone machine and you should find it.

Hope this helps,

Dave Mac

---

### Post by dmizer on 2009-03-18
Since you already have a virtual environment, why not just add a streaming music server like [gnump3d](http://gnump3d.sourceforge.net/)? It's in the repositories: [http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html](http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html)

---

### Post by whitethorn on 2009-03-18
When you start VirtualBox you can click on your XP machine, then to go settings.  Then choose the tab Shared Folders.  Here you can set which ever folders you want to share with your client (XP).  Then in XP click on network, virtual box shares and you should see the folders there. Unless you don't already use samba shares, no real need to set them up.

---

