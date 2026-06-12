---
title: "home sub-folder paths"
date: 2011-04-04
forum: Desktop Environments
---

### Post by MyD0j0 on 2011-04-04
Hey all!  Sorry if this has been asked/answered--I hadn't found what I was looking for so here's the question...  I'm running 10.10 and am curious about the folders listed under home.

I have a FreeNAS machine with all my movies, pics & music.  In nautilus, I was able to update the bookmarks for these folders.  Now I'd like the folders in my home directory (i.e., /home/me/music) to also point to them and I'd like to keep the same folder icons.

I thought there might be something in .profile, but didn't see anything that I thought would help (and not even sure that would be the proper place to indicate such a change).  How do I redirect the system to look in a different physical location for those folders--such as when a browser is downloading a file, it goes to the downloads folder without having to reconfigure the different browsers I use (simple, I know, but why make 4 changes if its possible to make 1 change)?

Also, would Ubuntu One be affected by these kinds of changes?  Due to a lot of manual moving of files, the folders are empty, but I'd also like to have Ubuntu One sync them when they are pointed in the left direction.

Thanks!

---

### Post by oldfred on 2011-04-04
I mount a data partition with all my folders and then link the folder into /home. How are you mounting & what format are the partitions on your freeNAS?

You can directly mount partitions into /home, but they will appear twice in the left panel.

I now mount the data partition in /mnt/data so it does not appear twice. Music & Videos are folders inside my data partition.
And link with these commands:
ln -s /mnt/data/Music
ln -s /mnt/data/Videos
More info but with old mounting location.
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Is it a NTFS partition?

Shared NTFS partition:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by Krytarik on 2011-04-05
Please see my earlier post regarding a similar matter:
[http://ubuntuforums.org/showthread.php?p=10430718#post10430718](http://ubuntuforums.org/showthread.php?p=10430718#post10430718)

Whether or not that affects Ubuntu One, I really don't know.

Greetings.

---

