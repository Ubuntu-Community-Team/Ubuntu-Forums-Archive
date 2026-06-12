---
title: "Transmission torrent directory?"
date: 2009-04-14
forum: General Help
---

### Post by Rofii on 2009-04-14
I can't seem to be able to find the directory where Transmission stores torrents after they are opened? Is there a directory where the .torrent files are saved, or are they simply used and immediately deleted?

---

### Post by cariboo on 2009-04-14
The transmission torrents file is located in ~/.config/transmission/torrents. To navigate to that directory in Nautilus, open Places-->Home Foler and press Ctrl-h. This will reveal the hidden files and directories.

Jim

---

### Post by howefield on 2009-04-14
Load up transmission and select preferences from the Edit menu.

The current destination folder will be displayed (and can be changed) in the Torrents tab. I haven't changed mine from the default, which is the desktop.

---

### Post by Rofii on 2009-04-14
> **cariboo907 said:**
> The transmission torrents file is located in ~/.config/transmission/torrents. To navigate to that directory in Nautilus, open Places-->Home Foler and press Ctrl-h. This will reveal the hidden files and directories.

Jim

Thanks!

> **howefield said:**
> Load up transmission and select preferences from the Edit menu.

The current destination folder will be displayed (and can be changed) in the Torrents tab. I haven't changed mine from the default, which is the desktop.

I meant where are the .torrent files stored, not where the files downloaded are stored, but thanks for your help anyways :)

---

### Post by lovinglinux on 2009-04-14
Since you problem has been solved, I would like to recommend Deluge torrent client. Give it a try. I bet you won't be disappointed.

You can download the latest version installation file (deb) from [http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge)

IMO, Deluge is way much better than Transmission, is easy to configure, has a nice interface and all essential features (DHT, UPnP, PEX, Encryption, Blocklists, file selection/priority and more).

For more info [http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by ignatiusjreilly on 2010-01-23
> The transmission torrents file is located in ~/.config/transmission/torrents. To navigate to that directory in Nautilus, open Places-->Home Foler and press Ctrl-h. This will reveal the hidden files and directories.

I noticed there is no option in preferences to change this directory. Is there any other way to do this?

---

### Post by MiceMiceRabies on 2010-04-07
On top of changing the .torrent directory, Is there a way to change where the .torrent data locates the seeding files?  

I am trying to set up a box specificaly for seeding, I need to move my downloaded content and .torrent files to a new place on my network.

---

### Post by lovinglinux on 2010-04-07
> **MiceMiceRabies said:**
> On top of changing the .torrent directory, Is there a way to change where the .torrent data locates the seeding files?  

I am trying to set up a box specificaly for seeding, I need to move my downloaded content and .torrent files to a new place on my network.

Yes. I don't have Transmission installed right now, but there should be an option to select the watched folder and another to select the storage folder. Move the data first form each torrent properties, then make a backup of your .torrent files, then delete the original .torrents and change the watched folder to point to the new location. Transmission should load all torrents again and check the data files form the new location.

---

