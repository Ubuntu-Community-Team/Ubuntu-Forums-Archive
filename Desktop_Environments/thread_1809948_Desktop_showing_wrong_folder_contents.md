---
title: "Desktop showing wrong folder contents"
date: 2011-07-22
forum: Desktop Environments
---

### Post by xSpidey01x on 2011-07-22
My ~/Desktop is generally kept empty.

Yesterday on start resume from hibernate, it looked as if my encrypted home directory was unmounted; or at least instead of my $HOME contents I got a bunch of files related to this.

I rebooted the system, and since then my desktop has been rendering icons for every file in my home directory, but not updating the icons until the next reboot, if I change anything in $HOME while it is running.


I opened the gconf-editor and checked: the box for using the home dir as the desktop is **not** checked. I even tried toggling it and the option that controls drawing the desktop on/off in every possible combination. Nadda. The only thing that works is turning off drawing the desktop.



Any ideas?

---

### Post by BbUiDgZ on 2011-07-22
reset your gui settings

```
cd ~/
```
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by mcduck on 2011-07-22
> **BbUiDgZ said:**
> reset your gui settings

```
cd ~/
```
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Before you do that you might want to check the *~/.config/user-dirs.dirs* file, and make sure it has this line in it:
```

XDG_DESKTOP_DIR="$HOME/Desktop"
```

If it doesn't or the line points to wrong place, fix it and log out & back again.

---

### Post by xSpidey01x on 2011-07-22
> **mcduck said:**
> Before you do that you might want to check the *~/.config/user-dirs.dirs* file, and make sure it has this line in it:
```

XDG_DESKTOP_DIR="$HOME/Desktop"
```

If it doesn't or the line points to wrong place, fix it and log out & back again.

Spot on, thank you! Whatever the precise cause of this, _everything_ in this file was being defined as $HOME/ -!


I think that also explains in part, what has caused this. My settings are customized (e.g. ln -s ~/docs -> ~/Dropbox/Documents) Whatever happened with the encryptfs thing coming out of that hibernate, the standard ones (e.g. ~/Documents) were there. After the recent resettage event, I forgot to update .config/user-dirs.dirs after I removed the standard ones (including this time, ~/Desktop just for the hell of it).

When I rebooted the system and came back in, it reset everything to $HOME/. Which appears to be what xdg-user-dirs-update does for anything that is missing. Groan.


> **BbUiDgZ said:**
> reset your gui settings

```
cd ~/
```
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

I would rather hope that level of destructive reset isn't necessary after [something already did that in effect](http://ubuntuforums.org/showthread.php?t=1807301), the other day. Which is probably related to the root cause here.

P.S. that would be reset your "GNOME" settings, excluding whatever apps store stuff also under ~/.config and ~/.local/share.

---

