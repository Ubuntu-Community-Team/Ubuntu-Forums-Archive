---
title: "Restore /usr/share/pixmaps"
date: 2008-03-23
forum: Desktop Environments
---

### Post by robz0rz on 2008-03-23
Hello

In an attempt to get [these]("http://lokheed.deviantart.com/art/Tango-GNOME-Core-Image-Pack-38422263") pixmaps on my installation, I accidentally deleted all the pixmaps through a terminal using sudo. Luckily, I backed up the original folder a few minutes before.

All that's left in /usr/share/pixmaps is the folder structure (sudo rm */*/*/*/* didn't remove the folders). How can I restore the orignal pixmaps that I have backed up? The File Browser says I am not allowed to copy. Also, what would be the correct way of installing the pixmaps at the aforementioned link?

Thanks in advance

---

### Post by munkyeetr on 2008-03-23
So you have the old pixmaps directory completely backed up, including sub-folders?

I don't know 100%, so wait for someone else to confirm whether this would be okay, but I would:
```

gksudo nautilus /usr/share

```
Then I would delete the pixmaps directory completely, and copy the backup over in it's place.

Again, please wait for confirmation from someone else that this would be okay. I don't want to be responsible for wrecking something on your machine or making things worse.

---

