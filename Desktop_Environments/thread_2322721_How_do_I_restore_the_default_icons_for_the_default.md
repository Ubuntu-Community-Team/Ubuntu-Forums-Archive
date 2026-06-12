---
title: "How do I restore the default icons for the default folders?"
date: 2016-04-30
forum: Desktop Environments
---

### Post by MJae on 2016-04-30
I'm on a new installation of Xubuntu 16.04. This happened after Thunar crashed. I wanted to replace the Documents, Downloads, Music, and Pictures folder with shortcuts to similar folders to a different partition. Thunar crashed when I did a cut-and-paste on some of the files I needed to move. When I restored (from trash) the original folders because I decided I  wanted to keep them, their icons reverted to generic folder icons. I  tried deleting some of the rest of the default folders (Public,  Templates, Videos) but, as you can see, they restored properly. How do I  get the original specialized icons for the default folders?

[https://i.gyazo.com/3c478625dd081e211d53333bf7db3f25.png](https://i.gyazo.com/3c478625dd081e211d53333bf7db3f25.png)

---

### Post by poltiser2 on 2016-04-30
It would work better and easier if you mount the partitions as your original folders during installation or using disk utility...
mounted in fstab as for ex.: Documents - the target partition would always mount and open in thunar as Documents ;-)

---

### Post by xubu2 on 2016-05-02
[http://ubuntuforums.org/showthread.php?t=1679009](http://ubuntuforums.org/showthread.php?t=1679009)
Open **~/home/mjae/.config/user-dirs.dirs** and add the folders in the config file that you've deleted.

edit - Another one: [http://askubuntu.com/questions/94734/what-is-the-templates-folder-in-the-home-directory-for](http://askubuntu.com/questions/94734/what-is-the-templates-folder-in-the-home-directory-for)

---

### Post by MJae on 2016-05-02
> **xubu2 said:**
> Open **~/home/mjae/.config/user-dirs.dirs** and add the folders in the config file that you've deleted.

Thanks, that worked wonders. Now, the next question becomes... How did they get removed from there in the first place? (You know, so it won't have to happen again.) The others didn't get removed...

---

### Post by wildmanne39 on 2016-05-03
Please use thumbnails or url's when posting images because many people have slow internet connections and have trouble loading pages with large images on them.
Thanks

---

### Post by xubu2 on 2016-05-03
> **MJae said:**
> Thanks, that worked wonders. Now, the next question becomes... How did they get removed from there in the first place? (You know, so it won't have to happen again.) The others didn't get removed...

They get removed from the user-dirs.dirs config file automatically when you remove them, but not added back in if you recreate them again.
You can edit user-dirs.dirs manually or type in the terminal: **xdg-user-dirs-update **for that.

Cheers.

edit: If you delete the user-dirs.dirs config file and type in terminal: **xdg-user-dirs-update **everything is restored to the default and the maps are back after the next login.

---

