---
title: "KDE 4.3 keeps restoring my important paths to default"
date: 2009-10-24
forum: Desktop Environments
---

### Post by edke on 2009-10-24
Hello guys. 

This is my main issue with latest KDE 4.3 under Jaunty or latest Karmic. It keeps restoring my important paths defined in System Settings -> About me -> Paths to default values.

Everytime I change these settings to my desired values (I hate folders with uppercase), after restarting and logging back to my KDE account settings are restored and in my ~ folder there are new default folders created. 

I tried to edit ~/.config/user-dirs.dirs file, changing it's attributes so it can't be modified, but no luck. Everytime it's restored back to defaults and it's very annoying.

My ~/.config/user-dirs.dirs looks like this:

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
#
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by Zorael on 2009-10-24
Curious, works for me. You could change the defaults as a workaround, I guess. They're in /etc/xdg/user-dirs.defaults.

---

### Post by edke on 2009-10-24
Some light in the dark :) But not a solution :(

[http://kubuntuforums.net/forums/index.php?topic=3107197.0](http://kubuntuforums.net/forums/index.php?topic=3107197.0)

---

### Post by frubblezuck on 2010-01-10
I changed my paths to lower case names to match what was already present in my home dir. It asked if I wanted to move the files from the previously defined directory to the newly defined directory. Much to my dismay, my ENTIRE home directory was wiped. 

I thought "Oh what did you do, stupid user??" I used the path configurator under "About Me" as above...that's what I did. I repeated it...and you know what...it wiped my home directory AGAIN!

Good thing I have backups of what's in my home directory scattered across my network. But this is 100% occurring through using About Me to change the paths.

 I just upgraded last night to Karmic.

---

