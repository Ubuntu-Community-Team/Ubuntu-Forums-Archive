---
title: "mountind usb in windowmaker"
date: 2006-02-24
forum: Desktop Environments
---

### Post by liquid boy on 2006-02-24
in xfce, you can load "gnome-volume-manager" to get usb disks to appear automatically, and you can save session so that gnome-volume-manager loads on startup. i thought it would be similar with windowmaker, but obviously not, i can't get it to load on startup.
i tried the dockapp "mount.app" - but couldn't figure out how to get it to load usb devices (only seems to work for cd's and floppy disks)

---

### Post by lamego on 2006-02-24
You can always do the manual mount:
Plug the device
Check for the device path name with "sudo dmesg" .
And then mount it with:
```
sudo mkdir /media/usb
sudo mount /device_name /media/usb
```

---

### Post by liquid boy on 2006-02-28
hmm, a friend of mine suggested an easy solution (that worked)
i edited the file ~/GNUstep/Library/Windowmaker/autostart

and added the line
```
gnome-volume-manager &
```

works perfectly.

---

