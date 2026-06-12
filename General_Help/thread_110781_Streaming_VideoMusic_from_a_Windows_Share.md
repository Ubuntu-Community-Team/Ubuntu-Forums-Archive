---
title: "Streaming Video/Music from a Windows Share???"
date: 2005-12-31
forum: General Help
---

### Post by pugs on 2005-12-31
How would I go about streaming audio/video from a windows share?  I am using mplayer.  When I navigate to smb://mywindowsshare and try to open a file to play, It seems to want to download the file to a temp directory on my linux computer before it starts playing.  Even if I try to open a txt file it seems like it downloads it first and then opens it.

I am actually running Kubuntu...is this something that would be KDE related or does anyone have this problem with gnome as well?  I really have no clue.  Maybe there is a setting somewhere I am missing.

Any help would be greatly appreciated.

---

### Post by pharcyde on 2005-12-31
Are you trying to do this from nautilus?   I don't use nautilus but I suspect if you mount the network drive to a local folder then browse with nautilus u won't have this problem.

To mount a network folder try:
[B]
sudo mount -t smbfs -o username=someuser,password=somepass //computername/folder /localfolder[/B]  

After you have done that try opening media from the /localfolder where u mounted it and see if that works.

---

### Post by pugs on 2005-12-31
I am actually using Konqueror to navigate since its Kubuntu.  But this worked like a charm.  Thanks a ton.

I did have to grab the smbfs I think its called...package to get it up and running.

---

