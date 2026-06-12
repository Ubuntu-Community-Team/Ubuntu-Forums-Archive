---
title: "rsync error 23"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-08-14
Having a problem I don't understand.  I'm trying to backup my home partition to my usb hard drive using rsync.  I used the following command:

```
rsync -vurt --progress --delete /home/ed /media/maxtor/backups/home-backup
```

Many files were copied, and when I right click the original and new folders I get the same number of files and total size.  However, at the end of the rsync process I was left with this error message:

```
sent 49459983 bytes  received 4726 bytes  1433759.68 bytes/sec
total size is 21827944451  speedup is 441.28
rsync error: some files could not be transferred (code 23) at main.c(791)

```

Scrolling back through the logs (I can't view them all as not all have been retained in the buffer), it seems that the files that have been skipped are in .wine which I can understand:

```

skipping non-regular file "ed/.wine/dosdevices/c:"
skipping non-regular file "ed/.wine/dosdevices/d:"
skipping non-regular file "ed/.wine/dosdevices/e:"
skipping non-regular file "ed/.wine/dosdevices/f:"
skipping non-regular file "ed/.wine/dosdevices/h:"
skipping non-regular file "ed/.wine/dosdevices/z:"
skipping non-regular file "ed/.wine/drive_c/windows/profiles/ed/Desktop"
skipping non-regular file "ed/.wine/drive_c/windows/profiles/ed/My Documents"
skipping non-regular file "ed/.wine/drive_c/windows/profiles/ed/My Music"
skipping non-regular file "ed/.wine/drive_c/windows/profiles/ed/My Pictures"
skipping non-regular file "ed/.wine/drive_c/windows/profiles/ed/My Video"

```

But also there seem to have been some files that I see no reason why it can't rsync.

```
skipping non-regular file "ed/.quodlibet/control"

skipping non-regular file "ed/.icons/OSX/scalable/places/gnome-main-menu.png"
skipping non-regular file "ed/.icons/OSX/scalable/places/gnome-mime-x-directory-nfs-server.png"
skipping non-regular file "ed/.icons/OSX/scalable/places/gnome-mime-x-directory-smb-server.png"
skipping non-regular file "ed/.icons/OSX/scalable/places/server.png"
skipping non-regular file "ed/.icons/OSX/scalable/places/stock_folder.png"
skipping non-regular file "ed/.icons/vibrant/scalable/apps/terminal.svg"
skipping non-regular file "ed/.ion3/look.lua"
skipping non-regular file "ed/.kde/cache-PMSEH"
skipping non-regular file "ed/.kde/socket-PMSEH"
skipping non-regular file "ed/.kde/tmp-PMSEH"

```

How do I stop this error, and is it significant?

---

### Post by baka_rob on 2006-08-14
One thing that comes to mind is that, if they are soft links (shortcuts), rsync may not be following them to copy the actual file, so it just ignores them.  If you run ls -l against some of the files it thinks are "non-regular", does the output look somewhat like this:

```
lrwxr-xr-x 1 owner group      12 2006-08-14 08:36 somefile.png -> realfile.png
```

?  If so, you will need to modify your rsync commands to include the -l flag, and possibly some others (or maybe the -a flag).  Or, alternatively, you could make a tar archive of the directory (or directories) you wish to backup and then rsync the one file.  Tar may initially have similar problems following links, so you would need to tell tar to follow the links as well.

I'm not near Gnome right now, so I'm not aware how to distinguish links from real files in its gui, but hopefully that helps!

Just a thought!  Good Luck.

---

### Post by Lunar_Lamp on 2006-08-15
That does appear to be the problem! :-D

Now I just need to work out how to solve it.  I think I shall have to append a few lines to my script, and output the verbose info to a file so I can view all the skipped files (and tell it to ignore files I don't want, and work out proper ways of dealing with ones I do).

---

