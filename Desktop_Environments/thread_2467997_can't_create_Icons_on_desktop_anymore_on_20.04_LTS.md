---
title: "can't create Icons on desktop anymore on 20.04 LTS"
date: 2021-10-15
forum: Desktop Environments
---

### Post by johankrab on 2021-10-15
Icons created on desktop no longer visible.
Even toggle in the extensions doesn't help.
It only occurs in one user account others works fine.
The .desktop files are in the desktop folder. Also when create a new map on the desktop the map is created in the desktop directory but no icon is visable.
What can be the problem en can i repair/restore the desktop environment?

---

### Post by yancek on 2021-10-16
The reason this doesn't work by default is intentional as explained in the article at the link below.

[https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28](https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28)

The command below installs gnome shell extensions for desktop icon.  This is what I used and it worked for me.   My Desktop is now cluttered with 2 icons.

```
sudo apt install gnome-shell-extension-desktop-icons 
```

---

### Post by vanadium on 2021-10-17
This is not intentional: Ubuntu supports desktop icons through that Gnome Shell extension. Check first if your Desktop folder still has its "special status":

```

cat ~/.config/user-dirs.dirs | grep DESKTOP

```

The directory should be indicated as "$HOME/Desktop". If that is not the case, edit the file and adjust the path. If there is no output from the above command, add the entire line:
```

XDG_DESKTOP_DIR="$HOME/Desktop"

```

That could, or could not, be the cause of your issue.

---

### Post by johankrab on 2021-10-17
I solved the problem by saving the data of the user, removed user and home directory.
After that created the user and restored the data.
It looks fine now.

---

