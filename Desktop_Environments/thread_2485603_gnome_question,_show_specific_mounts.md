---
title: "gnome question, show specific mounts?"
date: 2023-04-03
forum: Desktop Environments
---

### Post by stevermann on 2023-04-03
[SIZE=2][FONT=arial]My Ubuntu installation has a couple of mounted drives that I don't want to show on my desktop, so I use: [/FONT][/SIZE]```
[COLOR=#000000][FONT=monospace]gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false[/FONT][/COLOR]
```[COLOR=#000000][FONT=monospace] [SIZE=2][FONT=arial]to hide them.  The problem is, this also hides the icon for any USB thumbdrives as well.[/FONT][/SIZE]

[SIZE=2][FONT=arial]Is anyone aware of how I can selectively hide the mounted SSD drives on the sidebar but not the USB thumb drives?[/FONT][/SIZE]

[/FONT][/COLOR]

---

### Post by deadflowr on 2023-04-03
Which Ubuntu release?
These things keep changing, so good to know which one.
On Ubuntu 22.04 you can try
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts-only-mounted true
```
Which should set only those drives that are currently mounted to show.
But I am not sure whether or not it works for newer releases. (or older releases either)

---

### Post by TheFu on 2023-04-03
In the fstab, you can specify which mounts are not shown in GUI tools, but you'll need to setup each mounted file system inside there.  
Google to the aid: [https://askubuntu.com/questions/1265483/x-gvfs-hide-in-fstab-to-hide-a-folder-in-file-system](https://askubuntu.com/questions/1265483/x-gvfs-hide-in-fstab-to-hide-a-folder-in-file-system)  
If you didn't already know it was possible, doubtful you'd be able to find it via google.  The option is **x-gvfs-hide**. Most of the other stuff in that link is poor practice.

---

