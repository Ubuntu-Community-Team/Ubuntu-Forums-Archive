---
title: "Accessing files on network with, say, Amarok"
date: 2008-12-15
forum: General Help
---

### Post by mollydoggy1971 on 2008-12-15
I have my audio files on an external hard drive which is connected to my Windows PC.  The drive, as well as the individual folders, are all accessible when I go to the file browser in Ubuntu.  I can open any audio file and it will play under Ubuntu.  What I would like to be able to do is access that drive/folder with Amarok, so that all my audio is made into a playlist in Amarok.  How do I set it up so that I can do this?  Amarok will not allow me to browse to any networked drive/folder.

Thanks,
Jeff

---

### Post by Mokoko on 2008-12-15
why it is not accessible ?

maybe you can run amarok from the console with administrative privileges

gksudo amarok

maybe you have another problem but try with that

 more details please !!!

---

### Post by mollydoggy1971 on 2008-12-16
> **Mokoko said:**
> why it is not accessible ?

maybe you can run amarok from the console with administrative privileges

gksudo amarok

maybe you have another problem but try with that

 more details please !!!

When it asks me where to search for audio files, it does not give me an option to search on any networked drives.  I'm not sure what else I can say about it.  Amarok is not the only program I run into this issue with, but it is the main one (the one I use most).

---

### Post by mollydoggy1971 on 2008-12-17
Help!
Please!

---

### Post by jerome1232 on 2008-12-17
You should be able to mount the share at boot time to a local folder by creating an fstab entry, I'd have to do a little research myself to come up with a suitable fstab entry so I'm going to look around right now. Might want to look around for how-to's on mounting samba shares yourself as well.

edit: [http://happylinuxthoughts.blogspot.com/2008/05/permanently-mount-samba-or-windows.html](http://happylinuxthoughts.blogspot.com/2008/05/permanently-mount-samba-or-windows.html) looks promising; you'll need smbfs installed (sudo apt-get install smbfs)

---

### Post by sloopveedub on 2009-05-25
With Amarok 2, you can go to Amarok > Play media...

On the left side of the window that pops up -- called "Places" -- one of the options is Network, which will allow you to browse your network.

"Network" isn't an option if you're trying to point Amarok to your Collection, however.  Got to auto-mount to do that, as far as I know.

---

### Post by lawentzel on 2009-07-05
There is a discussion on another forum that I think will address this issue.  Specifically, the post is at:

[http://ubuntuforums.org/showthread.php?t=1163683&highlight=networked+Hard+drive](http://ubuntuforums.org/showthread.php?t=1163683&highlight=networked+Hard+drive)

Look at post #6

[http://ubuntuforums.org/showpost.php?p=7306238&postcount=6](http://ubuntuforums.org/showpost.php?p=7306238&postcount=6)

Hope this helps.

---

