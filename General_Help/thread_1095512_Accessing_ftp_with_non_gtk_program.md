---
title: "Accessing ftp with non gtk program"
date: 2009-03-13
forum: General Help
---

### Post by rage9 on 2009-03-13
I'm using Netbeans for PHP development, the major problem is it's ftp support blows chunks.

The other bad part is that because it's a non gtk program it can see the ftp folder on my desktop that was created by going to Places-->Connect to Server.

Is there a way to get non gtk programs to see this folder?

---

### Post by khelben1979 on 2009-03-13
[Konqueror]("http://en.wikipedia.org/wiki/Konqueror") uses [the KDE enviroment]("http://en.wikipedia.org/wiki/Kde") and has no need of gtk afaik. Do you have KDE installed?

---

### Post by ju2wheels on 2009-03-13
It should be able to see that folder on your desktop fine. Look for it in /media/the_fold_on_your_desktop instead of /home/your_user_name/desktop/your_ftp_folder .

---

### Post by rage9 on 2009-03-13
No I don't have KDE installed, don't think that'd do much of anything.

The ftp folder is on my Desktop.  I can use it just fine.  But I can't even from the command line see the folder, which is really odd.

---

### Post by ju2wheels on 2009-03-13
Right I understand that but what Im saying is that what it does in order to accomplish that icon on your desktop is it mounts your ftp to another folder. So it might show up as an icon on your desktop but actually be located in your /media folder.

---

### Post by rage9 on 2009-03-13
Yes I know exactly what your saying, there are no extra folders in my Media folder.

---

### Post by cariboo on 2009-03-13
I would suggest you have a look in ~/.gvfs.

Jim

---

### Post by rage9 on 2009-03-13
> **cariboo907 said:**
> I would suggest you have a look in ~/.gvfs.

Jim

Oh that's the money shot!  Thanks Jim!

---

### Post by ju2wheels on 2009-03-13
Try the following:

```

sudo apt-get install curlftpfs
cd ~/Desktop
mkdir myftp
curlftpfs ftp://yourftp.com myftp/

```

edit: User and pass can be set in the url as well like: ```
ftp://user:pass@yourftp.com
```

---

