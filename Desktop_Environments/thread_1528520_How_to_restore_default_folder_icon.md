---
title: "How to restore default folder icon"
date: 2010-07-10
forum: Desktop Environments
---

### Post by libssd on 2010-07-10
Because Remastersys has a size limit for its backups, I exclude the Pictures folder. Therefore, when I do a restore, there is no pictures folder; when I create one, it gets the generic folder icon, rather than the folder icon that is normally associated with the Pictures folder. I know that through properties I can replace the folder icon with anything, but I have not been able to find where the generic pictures folder icon is stored. If I choose a specific icon, and change the icon theme, the custom icon remains. Further, when I make a bookmark for the new Pictures folder, it gets the generic folder icon, no matter what icon is assigned to the Pictures folder.

I have searched and searched without finding a solution to this tiny niggle. There **must** be a way to restore the generic Pictures folder icon, so that it changes with the icon theme.

---

### Post by drs305 on 2010-07-10
The ~/home/Pictures folder icon is found here:
*/usr/share/icons/Humanity/places/XX/folder-pictures.svg*
with XX being the size (24, 48, etc).

That's still a specific icon so I'm not sure if it provides you with what you are looking for.

---

### Post by libssd on 2010-07-10
> **drs305 said:**
> The ~/home/Pictures folder icon is found here:
*/usr/share/icons/Humanity/places/XX/folder-pictures.svg*
with XX being the size (24, 48, etc).

That's still a specific icon so I'm not sure if it provides you with what you are looking for.
No, it doesn't; that just uses the folder-pictures.svg icon from a specific icon theme, which is how I discovered this problem. I'm looking for a way to associate a "generic" folder-pictures.svg such that the icon automatically changes if the entire icon theme is changed.

---

### Post by PhilGil on 2010-07-10
Assuming you are using Gnome...


[LIST=1]
[*]Right click on the icon you want to restore and select "Properties"
[*]In the properties window, click on the image of the icon.  An icon selection window will open.
[*]In the icon selection window, click the "Revert" button.
[/LIST]

---

### Post by libssd on 2010-07-10
> **PhilGil said:**
> Assuming you are using Gnome...


[LIST=1]
[*]Right click on the icon you want to restore and select "Properties"
[*]In the properties window, click on the image of the icon.  An icon selection window will open.
[*]In the icon selection window, click the "Revert" button.
[/LIST]
No again. Because the Pictures folder was excluded from the backup, when I create a new Pictures folder, it gets the *generic* folder icon, which is what it reverts to if it has been changed.

You can see this happen if you take one of the places folders and copy it to the desktop: the desktop copy will have a generic folder icon.

---

### Post by libssd on 2010-07-10
> **PhilGil said:**
> Assuming you are using Gnome...


[LIST=1]
[*]Right click on the icon you want to restore and select "Properties"
[*]In the properties window, click on the image of the icon.  An icon selection window will open.
[*]In the icon selection window, click the "Revert" button.
[/LIST]
No again. Because the Pictures folder was excluded from the backup, when I create a new Pictures folder, it gets the generic folder icon, which is what it reverts to if it has been changed. For example, let's assume I have assigned folder-pictures.svg from the Human theme. Revert will restore the generic folder icon.

You can see this happen if you take one of the places folders and copy it to the desktop: the desktop copy will have a generic folder icon.

---

### Post by PhilGil on 2010-07-11
That's baffling to me.  If I recall correctly, a default Gnome/Debian install does not include the default folders (Documents. Pictures, Music, etc..) like Ubuntu does, but if you create a folder called "Pictures" it inherits the special icon if one is available in the current icon theme.

Have you tried to remove and reinstall the Humanity and Ubuntu-mono icon sets?  Have you checked to see if there are icons in your /home/*username*/.icons folder that are overriding the default icons (in /usr/share/icons)?

---

### Post by libssd on 2010-07-11
It is baffling -- which is why I posted the question here. /home/username/.icons is empty.

Following a hunch, I have made some progress, although I can't explain exactly why. Since the desired icons are always in /usr/share/icons/Themename/places/XX/folder-pictures.svg, I tried using different pathnames even though I didn't expect them to work; *e.g.*:

```
/usr/share/icons/Default/places/scalable/folder-pictures.svg
/usr/share/icons/places/scalable/folder-pictures.svg
/usr/share/icons/folder-pictures.svg
```

As expected, none of these produced a usable icon. However, when I provided a viable path: 

/usr/share/icons/Human/places/scalable/folder-pictures.svg

Both the icon in the Nautilus main panel, **and** the shortcut icons in the side pane and in the Places menu all displayed consistently. They are still tied to a specific theme, of course, but this is a halfway solution, and probably not worth obsessing over.

After getting this far, I ran bleachbit to delete all caches, with no change in the situation.

I'm going to stop obsessing about this, but hope that others will not, as I'm curious to know the explanation for the original behavior.

---

### Post by ceefour on 2010-11-15
> **libssd said:**
> Because Remastersys has a size limit for its backups, I exclude the Pictures folder. Therefore, when I do a restore, there is no pictures folder; when I create one, it gets the generic folder icon, rather than the folder icon that is normally associated with the Pictures folder. I know that through properties I can replace the folder icon with anything, but I have not been able to find where the generic pictures folder icon is stored. If I choose a specific icon, and change the icon theme, the custom icon remains. Further, when I make a bookmark for the new Pictures folder, it gets the generic folder icon, no matter what icon is assigned to the Pictures folder.

I have searched and searched without finding a solution to this tiny niggle. There **must** be a way to restore the generic Pictures folder icon, so that it changes with the icon theme.
I was also looking for this. Turned out to be pretty simple. (if you know where to look, of course.. and that's the hard part)

1. Delete the file "$HOME/.config/user-dirs.dirs"
2. Run "xdg-user-dirs-update"

For reference, here's a "proper" user-dirs.dirs file:

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

---

### Post by LittleJakub on 2011-02-13
there is a MUCH easier way (at least for ppl, who cannot find a way to delete the files u mentioned)- it's a soft called Ubuntu Tweak, it offers to restore the thing, and not only- it's a great "command center" for all kind of functions of Ubuntu :)

---

