---
title: "Odd permissions on fat32"
date: 2006-05-20
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2006-05-20
I have a windows fat32 partition which behaves strangely with permissions. The relevant line in /ect/fstab is
```

/dev/hda1       /media/hda1 vfat iocharset=utf8,umask=000      0     0

```
so i think everyone should have rw permissions on it. Instead I find that some directories are read-only, which is quite annoying. Moreover there's no apparent pattern I can find: simply some directories at random are read-only.
I don't know what kind of information can be useful here. If you have any idea, please ask.

---

### Post by Ramses de Norre on 2006-05-20
1) The umask should be 0000 instead of 000, the first digit declares the way of inputting the permissions (0=binary values) and the three others are the permissions.

2) I've noticed this issue too.. I don't know a solution for it though.

---

### Post by aysiu on 2006-05-20
I've seen this behavior before, and it has to do with mounting FAT within the /media or /mnt folders. Make it its own static folder instead.

Paste this into a terminal: ```
sudo umount /dev/hda1
sudo mkdir /fat_partition
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace this line: ```
/dev/hda1       /media/hda1 vfat iocharset=utf8,umask=000      0     0
``` with this line ```
/dev/hda1       /fat_partition vfat iocharset=utf8,umask=000      0     0
``` Save (control-x), confirm (y), and exit (Enter). ```
sudo mount -a
```

---

### Post by Nonno Bassotto on 2006-05-20
Thank you for your quick replies. I tried both methods, but nothing changed. Anyway I noticed that the pattern is random, but stay the same everytime I mount my disk.
Maybe I should just delete my windows partition... (actually I would do this if only I found replacements for PowerTab and GoogleEarth).

---

### Post by robcarr2 on 2006-05-20
I am having the same problem, hope someone comes up with a solution to it :(

---

### Post by robcarr2 on 2006-05-20
Hey I found a solution! Check this link

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Once your in that window that pops up you can access anything and everything with permissions :D

---

### Post by Nonno Bassotto on 2006-05-20
Yes, I knew that, but I shouldn't always browse my files as root. At least if this are common files. Anyway, this is the way I do, before I understand what's happening.

If you are new to browsing nautilus as root, you may find the following useful (this is an off-topic). First, you can add scripts in a special folder, and they will show in the context menu. Let me make this example. Create in your home a file named "Open as root" and insert the folling lines into it

```

for uri in "$NAUTILUS_SCRIPT_SELECTED_URIS"; do
    gnome-sudo "gnome-open $uri" &
done

```

Then make it executable with the command "chmod +x".
```

chmod +x Open\ as\ root

```

Finally, move it in the folder "/home/your_username/.gnome2/nautilus-scripts".
```

mv Open\ as\ root .gnome2/nautilus-scripts/

```

If you want to do this graphically, just enable hidden files (ctrl + h) in your home directory.

Now, whenever you click on a file or a directory with the right mouse button, in the menu, under scripts, you will find "Open as root", which will do what his name says. If the script doesn't show up, just visit with nautilus your scripts folder.

Actually this is far more powerful then adding "open as root". You can find with google a lot of nautilus scripts to do whatever you want. The process to install them is always the same: just make them executable and move them in the right folder.

---

### Post by robcarr2 on 2006-05-20
Thanks for that, may come in handy sometime :)

---

