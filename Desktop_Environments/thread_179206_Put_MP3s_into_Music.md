---
title: "Put MP3s into /Music"
date: 2006-05-19
forum: Desktop Environments
---

### Post by 3rdalbum on 2006-05-19
To reduce clutter in my home directory, I've created a new folder: /Music, to hold directories full of music.

Is there anything wrong with doing this? I'm the only user of the computer, although my father might eventually start using the computer and may want his own user account, at which point he'd be able to access the Music directory. I'd just like to know if it's a bad idea to put general stuff into the top-level of the filesystem. Otherwise, I might put pictures and stuff there too!

Also, one last thing: I've got my NTFS partition mounted in Ubuntu, in my fstab file. Under "options" I just have "default". The dump and pass fields just have 0 in them. Currently, in order to access the drive, I have to open Nautilus as root. Changing the permissions doesn't do anything, as NTFS is read-only. Is there any way I can have that partition accessable by non-root users?

---

### Post by xyz on 2006-05-19
This is a great site to check out about file permissions...among other things.
Good luck!
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Ramses de Norre on 2006-05-19
Mount the ntfs with a line similar to this one: ```
/dev/hda3       /media/hda3  ntfs    nls=utf8,umask=0222 0       0

``` change to the correct device node and mount point.

For the music folder: I have it set up exactely the same way, because my home partition was too small to hold all my music. It isn't a problem, just set the owner of the folder to yourself, you can also choose whether you want to give your father acces to the drive or not (or maybe read-only).

There is no real harm in creating folders under /, but mind they will be overwritten when you update to dapper for example (so back them up)..

---

### Post by aysiu on 2006-05-19
If your music is on the NTFS partition, you'll have to add and delete songs through Windows, as Ubuntu won't write (make changes) to NTFS.

But so you won't have to launch Nautilus as root, follow these instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

There's nothing wrong with mounting /music as a top-level folder. If it bothers you later, you can symlink it (in Windows, a "shortcut"; in Mac, an "alias") to a more convenient place for your father.

Just make sure you change ownership so that it's the same group as you and your father. For example, if you and your father belong to the group *users*, you would do ```
sudo chown -R 3rdalbum:users /music
```

---

### Post by 3rdalbum on 2006-05-20
Thanks for the help and support, I'm now listening to my music guilt-free and browsing my Windows partition without being root :-)

---

