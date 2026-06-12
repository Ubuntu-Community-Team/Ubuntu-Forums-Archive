---
title: "Move Desktop Folder"
date: 2007-08-25
forum: Desktop Environments
---

### Post by oomingmak on 2007-08-25
I hate the way that config data and user files are all thrown into the same 'Home' folder, so I have set up a separate partition for all my files (Documents, Audio, Video, Images etc) to keep them distinct from system & app settings dot files.

I'd now like move my Desktop folder, but I don't know how to do it because it's a special folder.

Can someone please tell me how to specify an alternative partition location for my Desktop folder?

I'd like to use** mnt/local/Data/UserName/Desktop **instead of **/home/UserName/Desktop**.

Thanks.

---

### Post by happy-and-lost on 2007-08-25
Presumably *ln -s /mnt/local/Data/UserName/Desktop* when in ~ would do the trick.

---

### Post by Wolki on 2007-08-25
> **happy-and-lost said:**
> Presumably *ln -s /mnt/local/Data/UserName/Desktop* when in ~ would do the trick.

Yes, that should work. In gutsy, as part of the xdg-user-dirs standard, there will be the possibility to setup the locations of special places such as the desktop and default directories for music etc. via the ~/.config/user-dirs.dirs text file.

---

### Post by oomingmak on 2007-08-26
> **Wolki said:**
> In gutsy, as part of the xdg-user-dirs standard, there will be the possibility to setup the locations of special places such as the desktop and default directories for music etc. via the ~/.config/user-dirs.dirs text file.
Thanks for the information.

I had read about the xdg spec for specifying user data locations for folders such as Documents, Music, Video etc. but I did not know that it would also allow you to specify where the desktop folder should be located.

---

### Post by oomingmak on 2007-08-26
> **happy-and-lost said:**
> Presumably *ln -s /mnt/local/Data/UserName/Desktop* when in ~ would do the trick.
It doesn't work.

Console just keeps saying "File exists".

---

### Post by happy-and-lost on 2007-08-26
You'll need to *rmdir ~/Desktop* first.

---

### Post by oomingmak on 2007-08-26
> **happy-and-lost said:**
> You'll need to *rmdir ~/Desktop* first.
Thanks for the advice.

I didn't think that rmdir would work (because I would be deleting the actual desktop that I was currently using) but I tried it and the desktop folder *was* deleted. I was then able to create the symlink.

It sort of works, but the icon looks ugly because the added symlink emblem has caused the desktop emblem to shift and clash with the text of the folder name. 

[[IMG]http://www.MyOnlineImages.com/Uploads/Images/2095358162500Desktop%20Folder.png[/IMG]]("http://www.MyOnlineImages.com/")

Additionally there is some weird and unpredictable behaviour with the new desktop folder location. For example, if I take a screenshot and save it to the desktop, nothing happens (the file never appears). However, I can save that screenshot to any other folder (e.g. Home etc) and the file appears just fine.

Just as well that they are finally allowing users to specify the location of special folders, as I'm not sure that I'd be happy using the symlink method given the strange behaviour that I'm encountering.

---

### Post by oomingmak on 2007-08-26
Could I use some sort of mount command instead of Sym linking?

:confused:

---

### Post by Wolki on 2007-08-26
> **oomingmak said:**
> Could I use some sort of mount command instead of Sym linking?

:confused:

You could probably do it with a "mount --bind"

First try the following:
```
sudo mount --bind /mnt/local/Data/UserName/Desktop /home/UserName/Desktop
```

If it works, you'll probably want to add it to your fstab. I didn't try this, but a look at the mtab suggests this:
```

/mnt/local/Data/UserName/Desktop /home/UserName/Desktop none rw,bind 0 0

```

---

