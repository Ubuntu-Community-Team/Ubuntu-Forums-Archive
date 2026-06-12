---
title: "Set user wine files to a different directory"
date: 2009-02-11
forum: General Help
---

### Post by powerplayground on 2009-02-11
Alright is there a way to set up wine so the /home/user/.wine directory is in a different directory? I want to have all of my wine apps on a shared partitions for multiple distros to use.

---

### Post by powerplayground on 2009-02-11
bump, any way to do this?

---

### Post by k3rnelmustard on 2009-02-11
Kinda.  Symlink it.  Let's say you want to install everything to a drive that's mounted on /mnt/shared, and you want your new folder to be called wineStuff.  Just run this:

```

mkdir /mnt/shared/wineStuff
rm -rf /home/user/.wine
ln -s /mnt/shared/wineStuff /home/user/.wine

```


Now wine will still write to /home/user/.wine, but when it does that, it will be redirected to /mnt/shared/wineStuff and actually be writing the stuff physically there instead of ur home directory.  Symlinks are great!

---

### Post by overlord.gaurav on 2009-02-11
Probably [this page]("http://wiki.jswindle.com/index.php/Advanced_Wine_Installation#Changing_the_location_of_Wine.27s_installation") should do the trick for you! =)

EDIT: Long things short:
```
export WINEPREFIX=/media/external_drive/wine

```
But, reading the information there is more advisable as the above command might not really work.
Cheers!

---

### Post by k3rnelmustard on 2009-02-11
Or you could do that.  That might be easier, though I really like symlinks so I would suggest that.  (They're really easy to administer, maybe slightly less voodoo than env vars if they were to get messed up for some reason which occasionally happens)

---

