---
title: "Deleted Desktop Folder in Home Directory, Gnome"
date: 2007-09-18
forum: Desktop Environments
---

### Post by delsvr on 2007-09-18
I deleted the Desktop folder in my home directory and now my Gnome Desktop displays every file in my home directory. How can I fix this? I tried recreating the Desktop directory, but it's not reverting back. It just shows my home directory, now with a Desktop folder.

delsvr

---

### Post by olejorgen on 2007-09-18
Siily question maybe, but you did restart X/computer after restoring the folder?

PS: Thanks for this "tip" though. I've been annoyed about the Desktop folder in home. I thought that I tried to delete it, but apparently not :)

---

### Post by Lord Illidan on 2007-09-18
Make a Desktop folder, then open a terminal and run

```
gconf-editor
```

Once there, navigate to /apps/nautilus/preferences and on the right pane, set desktop_is_home_dir to false.

---

### Post by bertvv on 2008-02-23
> **Lord Illidan said:**
> Make a Desktop folder, then open a terminal and run

```
gconf-editor
```

Once there, navigate to /apps/nautilus/preferences and on the right pane, set desktop_is_home_dir to false.

I got the same problem and tried your solution. My preferences in gconf-editor were set correctly, though. I was able to solve it by editing ~/.config//user-dirs.dirs and change the following line:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

### Post by igor.sinkovec on 2008-03-03
> **bertvv said:**
> I got the same problem and tried your solution. My preferences in gconf-editor were set correctly, though. I was able to solve it by editing ~/.config//user-dirs.dirs and change the following line:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

Yes, this did the trick for me, too (after restarting). It's also described in [http://ubuntuforums.org/showthread.php?t=581498](http://ubuntuforums.org/showthread.php?t=581498), which was my actual problem.

Thanx!

igor

---

### Post by bharadwaj on 2008-03-03
change the title of this thread to [solved]

---

