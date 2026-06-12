---
title: "Desktop and home are equal"
date: 2008-05-14
forum: Desktop Environments
---

### Post by linuxfan3 on 2008-05-14
Hi,
my home directory is shown as my desktop. so i have two desktops now. stuff in home is shown on the desktop. it doesnt help to create a new directory called "Desktop" in home. The special desktop icon at the directory is missing. how do i get my true desktop directory back and how do i tell ubuntu to set my home as home and not as desktop? the situation is because i deleted the desktop directory in my home directory. please, it doesnt make any sence!
help please!!!:confused:

---

### Post by webarchitect on 2008-05-14
The fact that you wrote it like a zigzag makes it even more confusing...really..

---

### Post by jakon on 2008-05-14
Try this:

1. Open ~/.config/user-dirs.dirs with a Texteditor (~ means your home directory - /home/linuxfan3 or something like that. If you can't see the .config directory, press CTRL+h to see all files starting with a dot)
2. Change the line XDG_DESKTOP_DIR=whatever to XDG_DESKTOP_DIR="$HOME/Desktop"
3. logout, login

---

### Post by Awalton on 2008-05-14
> **jakon said:**
> Try this:

1. Open ~/.config/user-dirs.dirs with a Texteditor (~ means your home directory - /home/linuxfan3 or something like that. If you can't see the .config directory, press CTRL+h to see all files starting with a dot)
2. Change the line XDG_DESKTOP_DIR=whatever to XDG_DESKTOP_DIR="$HOME/Desktop"
3. **alt+f2, nautilus --restart, press return.** 

Fixed ;).

---

### Post by linuxfan3 on 2008-05-15
> **jakon said:**
> Try this:

1. Open ~/.config/user-dirs.dirs with a Texteditor (~ means your home directory - /home/linuxfan3 or something like that. If you can't see the .config directory, press CTRL+h to see all files starting with a dot)
2. Change the line XDG_DESKTOP_DIR=whatever to XDG_DESKTOP_DIR="$HOME/Desktop"
3. logout, login

fixed THANK YOU jakon :)
how can i mark the issue as solved by the way :confused:

---

### Post by SkonesMickLoud on 2008-05-15
```
 gconftool -t bool -s /apps/nautilus/preferences/desktop_is_home_dir false
```

Works as well.  No logout/in needed.

---

### Post by Awalton on 2008-05-15
> **SkonesMickLoud said:**
> ```
 gconftool -t bool -s /apps/nautilus/preferences/desktop_is_home_dir false
```

Works as well.  No logout/in needed.

Unfortunately, the desktop can still be the home dir (really, any dir), even with that setting set to false. That setting is really superfluous since Nautilus 2.20 or so, as we follow the Base Directory Specification in Nautilus. I'm working on a patch to remove this altogether for this reason alone, see [GNOME bug 469614](http://bugzilla.gnome.org/show_bug.cgi?id=469614) to track this.

Also, either way you shouldn't have to log in/out, we do watch the above mentioned files for changes, but sometimes it takes a bit to pick up the new setting, so I just usually suggest people restart nautilus (nautilus --restart in a terminal or after pressing alt+f2, as mentioned above).

---

### Post by SkonesMickLoud on 2008-05-15
> **Awalton said:**
> Unfortunately, the desktop can still be the home dir (really, any dir), even with that setting set to false. That setting is really superfluous since Nautilus 2.20 or so, as we follow the Base Directory Specification in Nautilus. I'm working on a patch to remove this altogether for this reason alone, see [GNOME bug 469614](http://bugzilla.gnome.org/show_bug.cgi?id=469614) to track this.

Also, either way you shouldn't have to log in/out, we do watch the above mentioned files for changes, but sometimes it takes a bit to pick up the new setting, so I just usually suggest people restart nautilus (nautilus --restart in a terminal or after pressing alt+f2, as mentioned above).

Good to know.  Thanks.

---

