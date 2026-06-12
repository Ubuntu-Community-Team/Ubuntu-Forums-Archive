---
title: "Cannot access any folders,[Unable to find the requested file. Please check the spell]"
date: 2018-06-07
forum: Desktop Environments
---

### Post by samir038 on 2018-06-07
I was trying to delete few files from my desktop.All of a sudden all the files were deleted and none of the folders were  accessible.
Unable to open Documents,Downloads,Pictures,Music ,could see the below message

Unable to find the requested file. Please check the spelling and try again.
Unhandled error message: Error when getting information for file '/home/samir/Videos': No such file or directory

samir@samir-Inspiron-N4050:~$ cat .config/user-dirs.dirs
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"

Could someone let me know how to fix this?/

---

### Post by Bashing-om on 2018-06-07
samir038; Hello - Welcome to the forum .

What exact command did you run to remove "those" files ?

What shows for terminal commands:
```

ls -al /home/
ls -al /home/samir/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Here we see what might require rebuilding.

[INDENT]broke ubuntu
[INDENT][INDENT]you get to keep the pieces
[/INDENT][/INDENT][/INDENT]

---

