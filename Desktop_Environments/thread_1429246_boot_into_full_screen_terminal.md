---
title: "boot into full screen terminal"
date: 2010-03-13
forum: Desktop Environments
---

### Post by DestructionsRightHand on 2010-03-13
Is there an easy way to change a run level to just boot into terminal.  I don't need a GUI to log in or anything, just want a black and white screen to work in and if needed startx.  I feel the only way to get a better understanding of linux is to stop using the crutch of the gui

---

### Post by falconindy on 2010-03-13
Append 'text' to your kernel options in GRUB.

I suggest using a terminal multiplexer such as screen or tmux, if you want to actually be productive outside of X. A tiling window manager also helps facilitate this without being bulky like Gnome or KDE.

---

### Post by lidex on 2010-03-13
Have a go at this:
[http://ubuntuforums.org/showpost.php?p=8851454&postcount=3]("http://ubuntuforums.org/showpost.php?p=8851454&postcount=3")

---

### Post by asmoore82 on 2010-03-14
RedHat and derived systems adhere to the "Runlevel" concept where
runlevel 5 is full graphical and runlevel 3 is text.

Debian and its derivatives(like Ubuntu) just configure runlevel 2 to be
what is desired and stick with that.

This is one of those few situations where I have no preference,
I just go with the flow of the OS I'm using ;).

If you are running Ubuntu 9.04 and below, you can disable the gdm service like this:
```
sudo update-rc.d gdm disable
```

Starting with Ubuntu 9.10, gdm has completed the move to an [[COLOR="Purple"]Upstart[/COLOR]]("http://en.wikipedia.org/wiki/Upstart") job, so you can do this:
```
sudo mv /etc/init/gdm.conf{,.disabled}
```

---

