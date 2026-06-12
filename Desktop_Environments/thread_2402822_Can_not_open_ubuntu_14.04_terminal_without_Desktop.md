---
title: "Can not open ubuntu 14.04 terminal without Desktop directory?"
date: 2018-10-04
forum: Desktop Environments
---

### Post by allen-bradley on 2018-10-04
Can not open Ubuntu 14.04 terminal window without Desktop directory?

Remove ~/Desktop directory
right click in background and select 'Open in Terminal'
terminal window opens and closes 

select ctrl-alt-t, terminal does open in ~ directory
select menu, Utilities, Terminal, terminal does open in ~ directory

What is the method to correct this with out changing ~/.bashrc?
What file needs to be changed so all users on system 'Open in Terminal' opens in directory ~ not ~/Desktop?

---

### Post by ajgreeny on 2018-10-04
I am not certain from your post what exactly your problem is so give us some extra info please.

Did you remove your Desktop directory, and if you did, my first question is, Why?
What were you hoping to achieve?

Let's see the output of ```
cat ~/.config/user-dirs.dirs
``` which may give us a clue, but it may be that you have removed certain possible actions by removing ~/Desktop

---

### Post by deadflowr on 2018-10-05
open in terminal is a nautilus add-on extension on 14.04 which used a gconf setting.

Install gconf-editor
open it and go to apps >> nautilus open in terminal.
You should have an option to set it to open in home.
The default is off, set it to on (check in the check box)

It should open in home from then on.

This would only apply for the user that it was changed for.
You'd need to change it individually for each user with their own user session,
in order for all to have it set this way.

gconf was the older settings method(?) used, but was a slow transition into the newer dconf setting method(?), so there are somethings which didn't move to the new way yet
(such as the open in terminal setting.)
You might be able to "adjust the setting to apply for all in one shot by following the old gnome way on it here:
[https://projects-old.gnome.org/gconf/]("https://projects-old.gnome.org/gconf/")

hope it helps

---

### Post by allen-bradley on 2018-10-05
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
XDG_VIDEOS_DIR="$HOME/"

---

### Post by allen-bradley on 2018-10-07
> **deadflowr said:**
> open in terminal is a nautilus add-on extension on 14.04 which used a gconf setting.

Install gconf-editor
open it and go to apps >> nautilus open in terminal.
You should have an option to set it to open in home.
The default is off, set it to on (check in the check box)

It should open in home from then on.

This would only apply for the user that it was changed for.
You'd need to change it individually for each user with their own user session,
in order for all to have it set this way.

gconf was the older settings method(?) used, but was a slow transition into the newer dconf setting method(?), so there are somethings which didn't move to the new way yet
(such as the open in terminal setting.)
You might be able to "adjust the setting to apply for all in one shot by following the old gnome way on it here:
[https://projects-old.gnome.org/gconf/](https://projects-old.gnome.org/gconf/)

hope it helps

Thank you, for your excellent response to my specific questions!  Your very clear complete instructions allowed me to solve my issue.  I am looking through the URL you sent me to solve it globally.  I appreciate you sharing your knowledge!

---

