---
title: "apache webfolders and using the home dir"
date: 2006-08-25
forum: Desktop Environments
---

### Post by canardo on 2006-08-25
Hi

I have the usual LAMP setup installed and configured fine,

I would like to be able to use my laptop which is running dapper brilliantly, to do some web development

I have made a directory ian my home dir ~/webDev and symlinked this to /var/www/

My question is how can I make it so that I can place files from a usb pen into the home dir and then be able to access them via the web browser, without having to chmod them, I am sure it must be possible and I am just being stupid

Otherwise is there a gui way, to move folders to the /var/www directory without having to use the cmd line and sudo

Thanks

---

### Post by FuriousLettuce on 2006-08-25
As long as you're careful, you can launch nautilus as root:

```
gksudo nautilus /var/www
```

---

### Post by dmwit on 2006-08-25
Why not linking the other direction?  Like:
```
cd /var/www
sudo ln -s /home/funusername/subdir subdir
```
~d

---

### Post by Uluen on 2006-08-25
I'm lazy and usually do a ```
chown -R user:user /dir
```

---

