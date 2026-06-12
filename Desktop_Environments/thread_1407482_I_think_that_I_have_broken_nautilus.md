---
title: "I think that I have broken nautilus"
date: 2010-02-15
forum: Desktop Environments
---

### Post by Alf Stockton on 2010-02-15
I am using Karmic 2.6.31-17-generic in a Gnome environment.
I think that I have been stupid and because I found the folder ~/Desktop empty I deleted it and now I get the contents of my ~/ all over my home screen in X.
Have I managed to screw with Nautilus? and please tell me how I fix this?

---

### Post by mhgsys on 2010-02-15
I knew I saw that earlier today; 

Have a look here; 

[http://ubuntuforums.org/showthread.php?t=1407226&highlight=home+desktop](http://ubuntuforums.org/showthread.php?t=1407226&highlight=home+desktop)


edit: open a  terminal; typ
```
gksudo gedit ~/.config/user-dirs.dirs
``` 


make it look like this;
```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

