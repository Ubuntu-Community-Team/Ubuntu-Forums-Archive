---
title: "SFTP User"
date: 2008-12-28
forum: General Help
---

### Post by mark36ph on 2008-12-28
Hi all. I am running a ubuntu VPS and have 3 users. 1 is the root, 1 is my user ( as root is not recomended to use all time ) and another user ( lets call him Bob ). I am able to login with Bob to FTP but it gives access to everything on my server. I would like to limit this to only access files/folders in the directory " /home/mark/public_html/sitea.com/ ".

Does anyone know how I can do this?

I am using SFTP

Thanks

---

### Post by RealPSL on 2008-12-28
You may want to take a look at rssh. There are instructions here:

[http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html]("http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html")

You do not have to compile anything however you can simply install it using ```
sudo apt-get install rssh
```

---

