---
title: "Cannot unlink symlink to directory"
date: 2013-06-18
forum: Desktop Environments
---

### Post by jmcgee on 2013-06-18
I want to remove a symlink to a directory, after that I will create another symlink. 

I get errors:

```
mythuser@PVR1:/usr/share/zoneminder$ ls -li
total 48
2876739 drwxr-xr-x 2 root root 4096 Dec 30 15:06 ajax
2876993 lrwxrwxrwx 1 root root   17 Feb 12  2012 cgi-bin -> ../../lib/cgi-bin
2876747 drwxr-xr-x 2 root root 4096 Dec 30 15:06 css
2876697 drwxr-xr-x 2 root root 4096 Dec 30 15:06 db
2876990 lrwxrwxrwx 1 root root   28 Jan 20 10:00 events -> /mnt/raid2/zoneminder/events
2876751 drwxr-xr-x 2 root root 4096 Dec 30 15:06 graphics
2876991 lrwxrwxrwx 1 root root   28 Jan 20 10:01 images -> /mnt/raid2/zoneminder/images
2876755 drwxr-xr-x 2 root root 4096 Dec 30 15:06 includes
2876988 -rw-r--r-- 1 root root 3795 Feb 12  2012 index.php
2876763 drwxr-xr-x 2 root root 4096 Dec 30 15:06 js
2876766 drwxr-xr-x 2 root root 4096 Dec 30 15:06 lang
2876787 drwxr-xr-x 5 root root 4096 Dec 30 15:06 skins
2876989 drwxr-xr-x 2 root root 4096 Feb 12  2012 sounds
2876992 lrwxrwxrwx 1 root root   26 Feb 12  2012 temp -> /var/cache/zoneminder/temp
2876984 drwxr-xr-x 2 root root 4096 Feb 12  2012 tools
2876985 drwxr-xr-x 2 root root 4096 Dec 30 15:06 views

```
```

mythuser@PVR1:/usr/share/zoneminder/events$ unlink /mnt/raid2/zoneminder/events
unlink: cannot unlink `/mnt/raid2/zoneminder/events': Is a directory
```

or 
```
mythuser@PVR1:/usr/share/zoneminder/events$ rm /mnt/raid2/zoneminder/events
rm: cannot remove `/mnt/raid2/zoneminder/events': Is a directory
```

or 
```
mythuser@PVR1:/usr/share/zoneminder/events$ rmdir  /mnt/raid2/zoneminder/events
rmdir: failed to remove `/mnt/raid2/zoneminder/events': Directory not empty

```

---

### Post by claracc on 2013-06-19
As I understand from the error obtained you are trying to unlink a directory but you have to unlink a FILE: [http://manpages.ubuntu.com/manpages/lucid/man1/unlink.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/unlink.1.html)

Also, this link can be useful: [http://manpages.ubuntu.com/manpages/lucid/man2/unlink.2.html](http://manpages.ubuntu.com/manpages/lucid/man2/unlink.2.html)

---

### Post by steeldriver on 2013-06-19
It looks like you are specifying the wrong 'end' of the link - if you have

```
/path/to/symlink -> /path/to/real/dir
```

then you shouldn't be trying to unlink or rm [FONT=courier new]/path/to/real/dir[/FONT], you should be doing

```
unlink /path/to/symlink
```

or

```
rm /path/to/symlink
```

In your case (since you are already in the parent dir), it should be enough to do

```
unlink events
```
or
```
rm events
```

---

### Post by jmcgee on 2013-06-19
Thanks Steeldriver, you were correct.  However, it deleted the directory, not just the symlink:

```
mythuser@PVR1:/usr/share/zoneminder$ ls -li
total 48
2876739 drwxr-xr-x 2 root root 4096 Dec 30 15:06 ajax
2876993 lrwxrwxrwx 1 root root   17 Feb 12  2012 cgi-bin -> ../../lib/cgi-bin
2876747 drwxr-xr-x 2 root root 4096 Dec 30 15:06 css
2876697 drwxr-xr-x 2 root root 4096 Dec 30 15:06 db
2876990 lrwxrwxrwx 1 root root   28 Jan 20 10:00 events -> /mnt/raid2/zoneminder/events
2876751 drwxr-xr-x 2 root root 4096 Dec 30 15:06 graphics
2876991 lrwxrwxrwx 1 root root   28 Jan 20 10:01 images -> /mnt/raid2/zoneminder/images
2876755 drwxr-xr-x 2 root root 4096 Dec 30 15:06 includes
2876988 -rw-r--r-- 1 root root 3795 Feb 12  2012 index.php
2876763 drwxr-xr-x 2 root root 4096 Dec 30 15:06 js
2876766 drwxr-xr-x 2 root root 4096 Dec 30 15:06 lang
2876787 drwxr-xr-x 5 root root 4096 Dec 30 15:06 skins
2876989 drwxr-xr-x 2 root root 4096 Feb 12  2012 sounds
2876992 lrwxrwxrwx 1 root root   26 Feb 12  2012 temp -> /var/cache/zoneminder/temp
2876984 drwxr-xr-x 2 root root 4096 Feb 12  2012 tools
2876985 drwxr-xr-x 2 root root 4096 Dec 30 15:06 views
```

then I did

> mythuser@PVR1:/usr/share/zoneminder$ unlink /usr/share/zoneminder/events
unlink: cannot unlink `/usr/share/zoneminder/events': Permission denied
mythuser@PVR1:/usr/share/zoneminder$ sudo unlink /usr/share/zoneminder/events
[sudo] password for mythuser: 

but it deleted the source directory, in addition to the symlink.  Not a big deal, there was nothing of importance in the directory, I just recreated it.

```
mythuser@PVR1:/usr/share/zoneminder$ ls -li
total 48
2876739 drwxr-xr-x 2 root root 4096 Dec 30 15:06 ajax
2876993 lrwxrwxrwx 1 root root   17 Feb 12  2012 cgi-bin -> ../../lib/cgi-bin
2876747 drwxr-xr-x 2 root root 4096 Dec 30 15:06 css
2876697 drwxr-xr-x 2 root root 4096 Dec 30 15:06 db
2876751 drwxr-xr-x 2 root root 4096 Dec 30 15:06 graphics
2876991 lrwxrwxrwx 1 root root   28 Jan 20 10:01 images -> /mnt/raid2/zoneminder/images
2876755 drwxr-xr-x 2 root root 4096 Dec 30 15:06 includes
2876988 -rw-r--r-- 1 root root 3795 Feb 12  2012 index.php
2876763 drwxr-xr-x 2 root root 4096 Dec 30 15:06 js
2876766 drwxr-xr-x 2 root root 4096 Dec 30 15:06 lang
2876787 drwxr-xr-x 5 root root 4096 Dec 30 15:06 skins
2876989 drwxr-xr-x 2 root root 4096 Feb 12  2012 sounds
2876992 lrwxrwxrwx 1 root root   26 Feb 12  2012 temp -> /var/cache/zoneminder/temp
2876984 drwxr-xr-x 2 root root 4096 Feb 12  2012 tools
2876985 drwxr-xr-x 2 root root 4096 Dec 30 15:06 views
```

Is there a command to just delete the symlink?

---

### Post by CharlesA on 2013-06-19
```
rm -i /path/to/symlink
```

;)

Use sudo if needed.

---

### Post by steeldriver on 2013-06-19
What do you mean exactly by "it deleted the directory"? Is /mnt/raid2/zoneminder/events still there? That's "the directory", and that should NOT have been deleted by either an unlink OR rm of the symlink

Or were you expecting /usr/share/zoneminder/ to still contain an 'events' dir?

---

### Post by jmcgee on 2013-06-19
Yes, I expected /usr/share/zoneminder/events as a directory to remain, but no longer be symlinked to /mnt/raid2/zoneminder/events.

It certainly is no longer symlinked but as you can see in the directory listing above, it was there before and not after the unlink command.

---

