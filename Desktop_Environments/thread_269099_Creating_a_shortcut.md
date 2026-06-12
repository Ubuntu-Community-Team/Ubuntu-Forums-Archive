---
title: "Creating a shortcut"
date: 2006-10-01
forum: Desktop Environments
---

### Post by pod25 on 2006-10-01
How do I create a shortcut for a mounted drive.
I would like a shortcut creating in another folder so it points to a mounted drive.
example :
```
/home/media/windows/MP3
```
Then the shortcut would be placed at
```
/etc/skel/ftp-skel/<short-cut-to-MP3>
```

I hope that makes sense.

---

### Post by Matodo on 2006-10-01
```
sudo ln -s /home/media/windows/MP3 /etc/skel/ftp-skel
```

---

### Post by pod25 on 2006-10-01
> **Matodo said:**
> ```
sudo ln -s /home/media/windows/MP3 /etc/skel/ftp-skel
```

I followed your instructions and it has indeed created a link of some form, however when I try to access it I get :
```
The Link "MP3" is Broken. Move it to Trash
```
So when I try to move it to trash I get
```
Error while moving. (Permissions)
```

---

### Post by pod25 on 2006-10-01
OK I have fixed the error now, it was my fault, I used the wrong path.
However my aim is to create a skeleton folder for my ftp server, and so far things are working, i just run my script and the account is created and it copies the contents of the skeleton folder to the users /home/folder, Now I just checked my test-account via ftp, I tried to access the shortcut links to the mounted drives and I now get:

No such File or Directory ????

Any ideas anyone ?

---

