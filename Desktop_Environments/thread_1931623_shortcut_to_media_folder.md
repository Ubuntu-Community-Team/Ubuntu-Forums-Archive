---
title: "shortcut to media folder?"
date: 2012-02-25
forum: Desktop Environments
---

### Post by thatguymark on 2012-02-25
So I have a Virtualbox VM with Xubuntu 11.10, got guest addition installed and have the share folder auto mounting in the media folder. I just would like to know how to have a shortcut on the desktop that goes there so I can more conveniently share files with the host machine?

Or can you just make a shortcut to a media folder?

---

### Post by 3Miro on 2012-02-25
If you set the share folder to be automatically mounter (or I think permanent), then every time you boot into Xubuntu you will have a folder /media/YouSharedFolder.

From there you need to make a symbolic link to the desktop. Open the terminal (Applications -> Accessories -> Terminal) and type:
```
ln -s /media/SharedFolder ~/Desktop/ 
```
Change the name "SharedFolder" to the name of your actual shared folder.

---

### Post by thatguymark on 2012-02-25
Thanks 3Miro. With that command though I get this:

> ln: `/media/sf_share': hard link not allowed for directory

---

### Post by thatguymark on 2012-02-25
Just some additional info if it might help: I had added my account to the vboxsf to enable the share folder to work with the host machine, and I just tried that command again with sudo in the beginning and it did create a shortcut on the desktop, but it's asking for an app to open it rather than just opening the folder..

Thanks to anybody who can help, still know very little about Linux but trying.

EDIT: NM I think it worked with sudo, I just forgot to change it to my folder name the second time!

---

### Post by 3Miro on 2012-02-26
> **thatguymark said:**
> Thanks 3Miro. With that command though I get this:

Did you put the "-s" option. I don't think it should have asked for sudo unless you don't have permissions to open the folder in the first place. Anyway, glad it works now.

---

