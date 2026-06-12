---
title: "random windows files being created"
date: 2009-04-25
forum: General Help
---

### Post by sindhu_sundar on 2009-04-25
hi i noticed that latley on all my partitions that are mounted, random files are being created automatically and that deleting them has no effect as they created again

sindhu@harish-desktop:/media/mixed-media$ ls
Completed Torrents     fvwrnf.exe  kht              stlqgw.exe
Currently Downloading  khs         Queued Torrents
sindhu@harish-desktop:/media/mixed-media$ cd ..
sindhu@harish-desktop:/media$ ls
cdrom  cdrom0  home  mixed-media  movies  music  root  spare  swap-space
sindhu@harish-desktop:/media$ cd movies/
sindhu@harish-desktop:/media/movies$ ls
fvwrnf.exe  khs  kht  stlqgw.exe
sindhu@harish-desktop:/media/movies$ cd ..
sindhu@harish-desktop:/media$ cd music
sindhu@harish-desktop:/media/music$ ls
English  fvwrnf.exe  Hindi  Kannada  khs  kht  stlqgw.exe  Tamil
sindhu@harish-desktop:/media/music$ cd ..
sindhu@harish-desktop:/media$ cd spare
sindhu@harish-desktop:/media/spare$ ls
Completed Downloads    fvwrnf.exe  kht                   Software
Currently Downloading  khs         Queued Torrent Files  stlqgw.exe
sindhu@harish-desktop:/media/spare$ cd ..
sindhu@harish-desktop:/media$ 

Please help.
thanks

---

### Post by Miyavix3 on 2009-09-19
The files seem to be created by Windows, or your Linux likes to make .exe files. Any more info? If not, this is not a Linux problem.

---

### Post by prshah on 2009-09-19
> **sindhu_sundar said:**
> hi i noticed that latley on all my partitions that are mounted, random files are being created automatically and that deleting them has no effect as they created again


That's chilling. Can your _linux_ be infected? 

Post the output of the below command```
sudo lsof | grep -i "\.exe"
```

Are you running any processes in Wine (Eg, uTorrent?) Or any P2P applications (Eg Limewire, FrostWire)?

Do these files appear only in your /media or even in your home directory? They should not appear in your home directory if a wine-based program is the culprit.

Are you running Ubuntu as a guest in a Windows host? (You can ignore this question if you don't get what it means)

---

