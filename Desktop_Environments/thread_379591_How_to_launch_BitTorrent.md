---
title: "How to launch BitTorrent?"
date: 2007-03-08
forum: Desktop Environments
---

### Post by lynwgnr on 2007-03-08
Hello I installed Ubuntu 6.06 Desktop for x86 using defaults, and by chance, I notice from Applications > Add/Remove that BitTorrent is installed. It was listed under the "Internet" category. Yet, I am unable to find it in Applications > BitTorrent. How do I launch it?
Thank you!

---

### Post by bruenig on 2007-03-08
It is launched when you double click a .torrent file. If you want a more configurable torrent client that you can just launch by itself, install azureus or ktorrent or utorrent through wine perhaps. There are some others also, those are just the main ones.

---

### Post by Qew on 2007-03-08
> **lynwgnr said:**
> Hello I installed Ubuntu 6.06 Desktop for x86 using defaults, and by chance, I notice from Applications > Add/Remove that BitTorrent is installed. It was listed under the "Internet" category. Yet, I am unable to find it in Applications > BitTorrent. How do I launch it?
Thank you!

In a console, the command is btdownloadcurses. In a console or xterm, use cd to change to the directory that the torrent file resides (eg, cd /home/lynwgnr/Desktop/), then run "btdownloadcurses blah.torrent" (no quotes). Use man btdownloadcurses for various options. However, if you want a user-friendly GUI, then install the BitTorrent GUI frontend "sudo apt-get install bittorrent-gui" (no quotes). It should put an item in your menu under Network.

Also, maybe I suggest installing bittornado, which has a few more options than the standard BitTorrent client. You'll find it in Synaptics or use apt-get to install it ("sudo apt-get install bittornado bittornado-gui").

---

### Post by lynwgnr on 2007-03-08
Thanks, you all are awesome! :)

---

