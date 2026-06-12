---
title: "How to change chinese folder name into english?"
date: 2013-02-14
forum: Desktop Environments
---

### Post by KooriNyann on 2013-02-14
I installed Chinese desktop environment and the folder name was all chinese such as "&#25991;&#26723;"(Documents)&#65292;"&#26700;&#38754;"(Desktop) and so on.

for example if i want to know what file(s) in Desktop folder, I have to write down an "ll" then open Chinese input method to spell a "&#26700;&#38754;" and press enter key, It is very inconvenient way to input a command in term window.

and if I switched into terminal environment, i can not input any Chinese character at all and chinese are displayed with diamonds...

what should i do? I am really do not want to reinstall the whole system again...

---

### Post by zombifier25 on 2013-02-14
One way is to change the language back to English, log out, and when it asks, change the folder's name to English. After that, change it to Chinese again, log out, and when you're asked to change the folders' name, deny.


Another way, which is sure to work (but takes a lot of manual editing), is to edit the file ~/.config/user-dirs.dirs . For English, the content should look like this:
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

And then rename the Chinese folders to their English names, log out, and log back in.

---

### Post by KooriNyann on 2013-02-15
> **zombifier25 said:**
> One way is to change the language back to English, log out, and when it asks, change the folder's name to English. After that, change it to Chinese again, log out, and when you're asked to change the folders' name, deny.


Another way, which is sure to work (but takes a lot of manual editing), is to edit the file ~/.config/user-dirs.dirs . For English, the content should look like this:
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```And then rename the Chinese folders to their English names, log out, and log back in.


It works!:smile:
And now, I can use folder in English name.

But there is still a problem: diamonds are still here in term mode.
Attached file is one screen-shot to describe the problem for your information
Can I change the display into English? But I don not want to make any change on Desktop mode.

how to do that?

---

