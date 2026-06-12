---
title: "user-dirs.dirs not working"
date: 2009-03-03
forum: General Help
---

### Post by Tamlyn78 on 2009-03-03
I am running Ubuntu 8.10 and have different partitions on my hard drive corresponding to folders in my home directory, they are mounted in the /media directory as follows:

/media/Documents
/media/Music
/media/Pictures
/media/Videos

After editing the user-dirs.dirs file like so:

XDG_DESKTOP_DIR="/media/Documents/desktop"
XDG_DOWNLOAD_DIR="/media/Documents/desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="/media/Documents"
XDG_MUSIC_DIR="/media/Music"
XDG_PICTURES_DIR="/media/Pictures"
XDG_VIDEOS_DIR="/media/Videos"

the desktop now correctly displays files kept in my "/media/Documents/desktop" directory, but when I try to access the Documents, Music, Pictures and Videos folders from my home directory there is nothing there. I thought that the user-dirs.dirs file was supposed to allow to to change the default location of these directories. Any thoughts?

---

