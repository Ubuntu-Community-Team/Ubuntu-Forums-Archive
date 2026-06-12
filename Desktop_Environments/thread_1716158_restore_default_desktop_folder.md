---
title: "restore default desktop folder"
date: 2011-03-28
forum: Desktop Environments
---

### Post by kamaru44ken on 2011-03-28
I have a Windows Partition for my Windows system and another partition for my Ubuntu. All my data is located in another partition called User). What I did, in the home folder, I deleted the default user folders (Documents, Desktop, Videos,...) and created a link to to the folders in the User partition. So for Desktop, I created a link to User/Desktop folder, for Documents, I created a link in my home folder to the 'User/My Documents'. What happens now is that all the symlinks I have created appear in my desktop instead of the Desktop items I have in User/Desktop. Any idea how to restore the default desktop folder? I have removed the link to the User/Desktop in my home folder and created a new folder named Desktop and nothing happens. Any idea?

---

### Post by nshiell on 2011-03-28
Not sure what you mean, could you go into a terminal and goto ("cd" command) your home folder and type "ls -la" Paste the output here and tell us whats wrong as I don't understand your question

---

### Post by Copper Bezel on 2011-03-28
I think he's saying that when he removed the Desktop folder and replaced it with a symlink, Gnome didn't accept the symlink as the Desktop folder and is now displaying the contents of his Home folder. He needs to set the path to Desktop again in gconf or restore it to the Default Folders list, but I'm not certain which one.

The list of Default Folders is the file /home/[username]/.config/user-dirs.dirs . It may or may not still have the Desktop folder listed, and it would be the thing to edit if you want to move your Desktop to another location via symlink. However, there's a setting in gconf-editor somewhere that you can toggle to show the contents of home/[username] instead of Desktop, and that might have been flipped, and I can't remember where it is or find it with searching.

The same function is in Ubuntu Tweak, under Desktop Icon Settings, so you should be able to change it there if you have ubuntu-tweak installed.

---

### Post by hariks0 on 2011-03-28
Install Ubuntu-tweaks and redefine the default folders using it.

---

### Post by Krytarik on 2011-03-28
The Gconf key Copper was referring to is: "/apps/nautilus/preferences/desktop_is_home_dir"

To make sure it is disabled just run this command:
```
gconftool-2 /apps/nautilus/preferences/desktop_is_home_dir --type bool --set false
```It should be possible to have a symlink pointing to the target desktop directory, maybe you just logged in one time upon changing that structure when the original desktop directory was already removed, and the symlink not already in place, resulting in no valid desktop directory for that session, making the user-dirs startup script change the settings.

For a better vividness, here is the content of the config file Copper was referring to, these are the default settings:

"~/.config/user-dirs.dirs":
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
But +1 for using Ubuntu Tweak for that, if you have it already installed.

Greetings.

---

