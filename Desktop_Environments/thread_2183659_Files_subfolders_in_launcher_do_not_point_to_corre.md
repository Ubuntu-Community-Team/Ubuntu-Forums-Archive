---
title: "Files subfolders in launcher do not point to correct location"
date: 2013-10-25
forum: Desktop Environments
---

### Post by PABlanche on 2013-10-25
Hi,

In the launcher bar, the "files" point to the correct "Home" folder. However, the submenu "document", "download", "music"...  all point to an incorrect folder giving the following error:
"Unhandled error message: Error when getting information for file '/home/_old/Downloads': No such file or directory"

I would like to correct this error, which basicaly is to replace the path "_old" to "_current"

I tried to open the Nautilus.desktop file but it is not there. I suspect a unity error but do not find the relevant file.

Thanks for your help.

---

### Post by mc4man on 2013-10-25
What does this show
```
cat .config/user-dirs.dirs
```

As far as nautilus.desktop it's in /usr/share/applications
Did you add a nautilus.desktop somewhere else like /usr/local/share/applications or ~/.local/share/applications

---

### Post by PABlanche on 2013-10-26
The location of the Nautilus.desktop file is indeed /usr/share/applications

```
cat .config/user-dirs.dirs
```

gives me 
```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
pablanche@pablanche-EliteBook:~$ 
```

---

### Post by PABlanche on 2013-10-28
I found the culprit. It was  .config/gtk-3.0/bookmarks

I used Searchmonkey to find the "_old" string inside files. The only place was that bookmarks. I open, change, and save it. Easy fix.

---

