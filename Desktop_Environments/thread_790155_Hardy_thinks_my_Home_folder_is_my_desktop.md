---
title: "Hardy thinks my Home folder is my desktop"
date: 2008-05-11
forum: Desktop Environments
---

### Post by larryni on 2008-05-11
I was playing around with the Wine desktop integration settings and somehow it renamed ~/Desktop folder to ~/Desktop.winecfg (or something similar) and I didn't notice it right away. The next time I rebooted Gnome switched to my Home folder and now displays all my files on the desktop. 

I reset the Wine settings and the Desktop folder has got its original name back, but I still can't get Gnome to use it. I had a look in gconf-editor to see if there was somewhere to change it, but couldn't see anything. 

Any ideas?

---

### Post by Zorael on 2008-05-11
I'm not sure Gnome reads this file, but open up [FONT="Courier New"]~/.config/user-dirs.dirs[/FONT] in a text editor and make manual modifications. Then log out and back in to see changes apply (or perhaps restart the desktop manager. [FONT="Courier New"]gdesktop[/FONT]?)

Should look something like this; fairly intuitive.
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="/home/zorael"
XDG_DOCUMENTS_DIR="/media/main/documents"
XDG_DOWNLOAD_DIR="/media/main/downloads"
XDG_MUSIC_DIR="/media/misc/audio"
XDG_PICTURES_DIR="/media/main/pictures"
XDG_PUBLICSHARE_DIR="/media/main/share"
XDG_TEMPLATES_DIR="/media/main/documents/templates"
XDG_VIDEOS_DIR="/media/main/anime"
```

---

### Post by TenPlus1 on 2008-05-11
Pop into [www.getdeb.net](www.getdeb.net) and download Ubuntu Tweak (unless you already have it)...  Their is an option that allows you to make your home folder into your desktop folder, so it's just a matter of turning it off and logging out and back in again...

---

### Post by larryni on 2008-05-11
Thanks to the both of you. My Desktop is back to normal :)

---

### Post by Yannick Le Saint kyncani on 2008-05-11
It's been a long time since I've last used gnome, but I remember a gconf boolean entry named "desktop_is_home_dir".

May it help you.

---

### Post by daniel014 on 2009-04-10
> **Yannick Le Saint kyncani said:**
> It's been a long time since I've last used gnome, but I remember a gconf boolean entry named "desktop_is_home_dir".

May it help you.

Yep, I've found that under apps > nautilus > preferences in Gconf-editor in Jaunty.

That was the way I learnt to show the Home Folder on the Desktop.

---

