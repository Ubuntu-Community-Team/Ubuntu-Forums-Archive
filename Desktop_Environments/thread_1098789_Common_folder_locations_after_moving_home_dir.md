---
title: "Common folder locations after moving home dir"
date: 2009-03-17
forum: Desktop Environments
---

### Post by vaibhav on 2009-03-17
Hi,

I recently moved the home directory of a user from /home/user to /home/usernew by modifying /etc/passwd. All works fine, except the common folder locations like Pictures, Documents, etc. still point to /home/**user**/Pictures instead of /home/**usernew**/Pictures. How do I make it point to /home/usernew/Pictures?

I'm using Ubuntu 8.04.

Also, is this a bug? The behaviour seems odd. Desktop correctly points to /home/usernew/Desktop, then why not Pictures etc.?

---

### Post by Zorael on 2009-03-17
Directories like those are generally defined in **~/.config/userdirs-dirs**. Open it up in a text editor and make sure they're entered correctly. References to your user directory should be **$HOME**, to translate correctly even after a username change, but considering the results you're getting perhaps they're entered as **/home/user** instead?
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
#
XDG_DOWNLOAD_DIR="$HOME/downloads"
XDG_MUSIC_DIR="$HOME/audio"
XDG_PICTURES_DIR="$HOME/pictures"
XDG_VIDEOS_DIR="$HOME/video"
XDG_DESKTOP_DIR="$HOME/desktop"
XDG_DOCUMENTS_DIR="$HOME/documents"
XDG_TEMPLATES_DIR="$HOME/documents/templates"
XDG_PUBLICSHARE_DIR="$HOME/share"
```

(Boo for uppercase! hiss!)

---

### Post by vaibhav on 2009-03-18
> **Zorael said:**
> ... but considering the results you're getting perhaps they're entered as **/home/user** instead?


I just checked the **~/.config/user-dirs.dirs** file and the paths there are relative to $HOME and not hard-coded wrt /home/user. Still the issue :(

To reiterate the problem, clicking **Places -> Pictures** still opens the old location. Maybe Nautilus' Places links are not picked up from user-dirs file, but from somewhere else?

---

