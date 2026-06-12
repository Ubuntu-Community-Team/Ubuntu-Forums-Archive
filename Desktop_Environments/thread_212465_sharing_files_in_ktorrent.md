---
title: "sharing files in ktorrent"
date: 2006-07-09
forum: Desktop Environments
---

### Post by djaya2 on 2006-07-09
Can I make ktorrent share files that I did not download through ktorrent?  I don't see a way to point it to a share directory---maybe bittorrents just don't work that way?  Thanks.

---

### Post by Jucato on 2006-07-10
Yes you can do that with KTorrent, though it takes a few extra steps as compared to other clients like the official Bittorrent client (not the one installed with Ubuntu).

Launch KTorrent. Go to File > Import existing downloads. In the dialog box that will pop up, search for:
a. the .torrent file of the file that you want to share; and
b. the file that was completed/finished downloading. If what you have is a single .torrent file that downloads multiple files (like multiple ISOs) in one single folder, instead of searching for the exact file, put in the location/folder of the files.
For example, if mytorrent.torrent downloads files a, b, and c in the directory /home/username/mytorrent/, then put in the second input box */home/username/mytorrrent/*

Hope I made it a bit clear. (It's hard to put some instructions into words. :D)

---

### Post by stoeptegel on 2006-07-10
> **Fenyx said:**
> Yes you can do that with KTorrent, though it takes a few extra steps as compared to other clients like the official Bittorrent client (not the one installed with Ubuntu).


This is going offtopic,
but perhaps it's nice to know that 2.0 will have both the import plugin and a new "auto import" function like mainline and others have.(current beta doesn't have it yet)

---

### Post by djaya2 on 2006-07-10
Thanks --- what if the files weren't originally downloaded as torrents?  I downloaded the Kubuntu .iso's from the web, so I don't have .torrent files for them.

---

### Post by stoeptegel on 2006-07-11
> **djaya2 said:**
> Thanks --- what if the files weren't originally downloaded as torrents?  I downloaded the Kubuntu .iso's from the web, so I don't have .torrent files for them.

This will only work if the downloaded iso by http/ftp, is exactly the same iso as they made for the bittorrent download.
If not, the hashes in the torrent file will not match the data and those chunks will get dumped without recovery. This will result in having to download the iso again. (fully by http/ftp or, if you're lucky, partial with a bittorrent client)

What i always do when i am not sure if the torrent will match the data: i just make a dupe of the data in another folder so there's a backup in case the hashing goes south. This takes about one minute or so, not a big deal...

---

### Post by vem0m on 2006-07-11
yea if u don't import and u load a torrent for an existing directory it overwrites it(deletes all data there in) and starts over it sucks it happened to me and i am left with either redownload or forget it so yea be careful

---

