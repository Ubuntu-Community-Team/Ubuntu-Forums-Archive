---
title: "Change music, movies, etc locations to external hard disk"
date: 2011-01-02
forum: Desktop Environments
---

### Post by Pithikos on 2011-01-02
I want to change my music, movies etc default location to my external hard drive. I opened the .config/user-dirs.dirs and have this:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```As my external hard disk is not always connected changing those locations will probably issue some problems. So is there a way to have a default value and a second value? Something in this manner:
```
XDG_MUSIC_DIR="/media/Iomega1TB/Music" OR "$HOME/Music"
```

---

### Post by ajgreeny on 2011-01-02
You could just make links from the default folders in your home to those in the external disk.  The only error that would then occur if the external disk was not attached is that the links would not actually point to anything and would show for that time as "Broken link", which would not matter too much.

---

