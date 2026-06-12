---
title: "Nautilus keeps crashing! Halp me guys!"
date: 2005-03-21
forum: Desktop Environments
---

### Post by Jonathan Drain on 2005-03-21
So I'm moving my stuff around in /mnt/stuff/, the FAT32 partition that used to be my Win2K partition, and decide to rename a folder - sorry, a directory - there from 'd&d' to 'D&D'. I do so using the standard GNOME directory-opening dealy, (Nautilus, I'm led to believe) and then I try to delete another directory, but it stalls on me. Ever since, I have been unable to open /mnt/stuff without it stalling on me.

I fire up a console and do an 'ls' and it turns out that the folder never actually renamed from d&d to D&D. I try renaming it command-line but it's fiddly with the ampersand so I rename it DnD. Even after this rename, I can't open /mnt/stuff in the GUI! I can open subdirectories, yeah, just not /mnt/stuff itself, and I can do things with /mnt/stuff in a console, just not with the interface.

If  it's any help, here's an ls of the directory.
```
jdigital@thundaril:/mnt/stuff $ ls -oa
total 772
drwxrwxrwx   15 root        32768 2005-03-21 16:40 .
drwxr-xr-x    4 root         4096 2005-02-20 13:27 ..
drwxrwxrwx   18 root        32768 2002-12-27 22:23 DnD
drwxrwxrwx    8 root        32768 2002-12-27 22:46 Finalfight
drwxrwxrwx   28 root        32768 2004-02-22 15:38 Manga and Doujins
drwxrwxrwx   16 root        32768 2002-12-27 22:44 Music
drwxrwxrwx    4 root       229376 2004-07-16 00:30 My Pictures
drwxrwxrwx    3 root        32768 2004-03-27 16:23 My Received Files
-rwxrwxrwx    1 root        99054 2005-02-17 02:11 new text dockeyment.txt
drwxrwxrwx    8 root        32768 2005-03-21 15:35 Old Stuff
drwxrwxrwx   19 root        32768 2002-12-27 22:40 Pics
drwxrwxrwx   14 root        32768 2002-12-27 22:35 Storage
drwxrwxrwx   23 root        32768 2004-11-13 02:09 Textfiles and Educational
drwxrwxrwx    9 root        32768 2003-01-16 02:33 Trashcan
drwxrwxrwx   13 root        32768 2002-12-31 19:15 Video
drwxrwxrwx   19 root        32768 2002-12-27 22:31 Wave

``` 

I thought I'd left this kind of crashing behind when I stopped using Windows! Is anyone here expert enough to solve this problem, or are these forums only able to answer basic questions?

---

### Post by lorap on 2005-03-21
hi friend!
if i understood well you weren't able to edit your fat32 partitions.am i right?
if so then do the next things to get it fixed:

i.create a directory, say "fat" in your home directory this way:

sudo mkdir /home/yourusername/fat

ii.now lets connect it to your windows partitions:

sudo mount /dev/hda0 /home/yourusername/fat -t vfat -o umask=000

that's all,now you're able not only view but edit everything in that partition.
if it would you popup an error message saying that such device doesn't exist or busy then try "hda1 or hda2" respectively.
to free the device you'd have all windows closed.then you write this:

sudo umount /dev/hda0 -f

that's all!
have a nice day friend!
pavel

p.s.:

-t vfat = means you're gonna connect to fat32.
-o umask=000 = gives you full read/write access.
sudo = gives you an administrative rights.

---

### Post by Jonathan Drain on 2005-03-21
That wasn't the problem.

However, I managed to fix it just now by making a new folder, moving some things into it and moving them back out again. I have no idea why this works, but it does.

Can anyone solve my other problem, which I've detailed in the following thread? (Click link to view) : [http://www.ubuntuforums.org/showthread.php?t=16718&page=1&pp=30](http://www.ubuntuforums.org/showthread.php?t=16718&page=1&pp=30)

---

