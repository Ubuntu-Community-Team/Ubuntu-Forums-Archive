---
title: "how to unmount icons from desktop"
date: 2010-08-29
forum: Desktop Environments
---

### Post by runescape on 2010-08-29
hello, 

i have this very annoying problem, sadly i tried couple of commands for auto-mounting, i thought it was safe, but now i have all these directories from /home/family showing on my desktop, even when i choose desktop from places>> it directs me to home/family, i surfed the forums and as far as i m guessing there should be something wrong in my fstab, here is what i have in fstab: 

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=af5138fa-1eae-49ca-af0f-158c7db4792d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=48550f9d-9549-4ca4-a313-63bd4b36582c none            swap    sw              0       0

am i in the right direction, what is the problem i have.

---

### Post by dv3500ea on 2010-08-29
I don't think this is a problem with fstab.

These steps may solve your problem:
[LIST=1]
[*]Go to Places -> Home Folder
[*]Press Ctrl+H to show hidden folders
[*]Double click the .config folder to open it
[*]Double click the user-dirs.dirs file to open it in the text editor
[*]Replace the line ```
XDG_DESKTOP_DIR="$HOME/family"
``` (or something similar) with the line ```
XDG_DESKTOP_DIR="$HOME/Desktop"
```
[*]Press Alt-F2 and enter ```
killall nautilus
```
[/LIST]

---

### Post by runescape on 2010-08-29
OH... you are a Genius , problem solved, thanks a lot man, i would wanna kiss u right now.:D

---

