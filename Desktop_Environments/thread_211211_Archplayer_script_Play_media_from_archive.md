---
title: "Archplayer script: Play media from archive"
date: 2006-07-07
forum: Desktop Environments
---

### Post by dyssident on 2006-07-07
Presenting Archplayer.

Archplayer is a Nautilus script that transparently extracts media files from archives then deletes them for you when you are done. Now you can keep your downloaded albums in their origional archives, allowing you to continue sharing them while saving you the loads of disk space that extracted copies would occupy. 

**Features**

- Extracts contents of archive and adds them to Totems playlist. 
- Archives added once Totem is running will be added to current playlist. 
- Once Totem is shut down, extracted files are automatically deleted.
- Only audio and video files are added to playlist.
- Runs as a Nautilus script
- Currently supports rar, zip, tar, tar.gz

**Installation**

Download the attached archplayer.tar.gz then run the following

```

tar -xzvf archplayer.tar.gz
cd archplayer
./deploy.sh

```

The packages rar and unzip will be installed, so you may need to provide your password. Then all you have to do is right click on an archive in nautilus, click scripts then Play Archive in Totem.

---

