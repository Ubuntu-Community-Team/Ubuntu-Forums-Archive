---
title: "can i change dimension of guest-home directory?"
date: 2009-05-13
forum: General Help
---

### Post by alepila on 2009-05-13
Hello, i would like to change the dimension of the directory guest-home assigned in guest-session because some files are over maximum dimension and i can't use they.

Thank you

---

### Post by stathol on 2009-05-13
The gdm-guest-session package is ... interesting. All of its scripts can be found in /usr/share/gdm/guest-session

I took a look at the guest-session-setup.sh script and this is what it does to set up the temporary user's home:

```
# create temporary home directory
HOME=`mktemp -td guest-home.XXXXXX`
mount -t tmpfs -o mode=700 none "$HOME" || { rm -rf "$HOME"; exit 1; }
chown $USER:$USER "$HOME"
cp -rT /etc/skel/ "$HOME"
chown -R $USER:$USER "$HOME"
usermod -d "$HOME" "$USER"
```

The guest user's home is a file mounted as tmpfs. Tmpfs should expand to accomodate whatever you put in there. I don't see anything in the script that should restrict the size of the guest user's $HOME.

How is /tmp itself set up on your machine? Is it just a directory off the root filesystem, or is it a separate filesystem/partition mounted onto /tmp?

Since the file that serves as the guest user's home was created with mktemp, it will reside in /tmp. So whatever size restrictions are in place for /tmp will also affect the guest user's home. Other than that, I don't know why there would be a size limit. :confused:

---

### Post by alepila on 2009-05-14
Hello, the /tmp directory is in the root file system, there isn't separated partition /tmp

---

