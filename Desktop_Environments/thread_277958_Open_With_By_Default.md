---
title: "Open With By Default"
date: 2006-10-15
forum: Desktop Environments
---

### Post by jpatt on 2006-10-15
I have a folder on my desktop named Pictures. I want to always open it with gThumb Image Viewer. Right click, properties, open with, lists gThumb and Open Folder. I cannot select gThumb even though it is listed. tip?

---

### Post by aysiu on 2006-10-15
Maybe for some strange reason you don't have ownership of it? ```
sudo chown -R jpatt:jpatt /home/jpatt/Desktop
``` Assumes your username is *jpatt*--substitute your actual username.

---

### Post by jpatt on 2006-10-15
is this right because I cannot get to work.

sudo chown -R jape:jape /home/jape/desktop/

cannot access no such file or directory

](*,)

---

### Post by aysiu on 2006-10-15
It's case-sensitive.

Notice the capital *D* in *Desktop*?

---

### Post by Kateikyoushi on 2006-10-15
I think gthumb simply can't be associated with opening folders.
I tried to associate it with some folders but I can't, and I have permissions on the folders.

---

### Post by jpatt on 2006-10-15
case sensetive was my issue, thanks. Like Kate said, it doesn't work. I can right click and open with gThumb. Not terribly inconvenient. Thanks all.

---

