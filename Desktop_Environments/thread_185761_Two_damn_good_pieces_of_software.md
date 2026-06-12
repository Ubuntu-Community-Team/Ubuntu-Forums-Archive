---
title: "Two damn good pieces of software"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Bou on 2006-06-01
Just seen those two packages at Joelbryan's site:

Ubuntu Common Hooker ([http://joelbryanonsoftware.blogspot.com/2006/05/5-ubuntu-common-hooker.html](http://joelbryanonsoftware.blogspot.com/2006/05/5-ubuntu-common-hooker.html)) will autoenable Multiverse and install any package you need to view a given file - e.g. if you download a .cbr comix and don't even know which program to install, it will install Comix and launch it.

Ubuntu Home Backup ([http://joelbryanonsoftware.blogspot.com/2006/05/3-ubuntu-home-backup.html](http://joelbryanonsoftware.blogspot.com/2006/05/3-ubuntu-home-backup.html)) is the app I've been searching for so long. It allows to easily backup your files and settings to any media you choose - including removable media.

Those are two crazy pieces of software IMO, is there a way to convince Ubuntu devs to include them for Edgy? Maybe then they can be backported to Dapper?

Also, I've got another question: I've tried to install Home Backup - which doesn't come as a .deb- but when I try to run ./configure, I just get this message: "configure: error: cannot find install-sh or install.sh in . ./.. ./../.."

Is there a way to actually get it working?

---

### Post by xyz on 2006-06-01
Hi Bou,
Someone had a similar problem here:
[http://www.ubuntuforums.org/showthread.php?t=20684&highlight=find+install-sh](http://www.ubuntuforums.org/showthread.php?t=20684&highlight=find+install-sh)
Hope it helps!
Your English is just great...signature included!

---

### Post by JoWilly on 2006-06-01
Thanks for pointing me to these links. This is indeed very nice.

---

### Post by cbudden on 2006-06-01
You need automake 1.9 (well I did) to get it to install.  Also, for some reason it tries to run ubuntu-home-backup-gui from /usr/libexec/ which does not exist.  So.
After sudo make install
```

sudo mkdir /usr/libexec/ 

```
now make sure you are in the src directory
```

sudo cp ubuntu-home-backup-gui /usr/libexec/ubuntu-home-backup-gui

```

---

### Post by Bou on 2006-06-01
[QUOTE=cbudden]You need automake 1.9 (well I did) to get it to install.[/QUOTE]

Thanks a lot, but now it's asking me for 'gtk+-2.0':

> checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

frandavid100@laptop:~/ubuntu-home-backup-0.1$

Where can I find it? Thanks again.

---

### Post by garba on 2006-06-01
hi bou, my guess is you need the dev package for gtk-2:

sudo apt-get install libgtk2.0-dev

---

### Post by Bou on 2006-06-01
[QUOTE=garba]hi bou, my guess is you need the dev package for gtk-2:

sudo apt-get install libgtk2.0-dev[/QUOTE]

Right on the nail!

Whoa this is THE backup tool!

---

### Post by ketsugi on 2006-06-02
That backup tool looks nice; someone really should put together a .deb for it.

---

### Post by simplyw00x on 2006-06-02
> someone really should put together a .deb for it
Someone has. Oh snap!

[http://www.moho.frihost.net/home-backup/](http://www.moho.frihost.net/home-backup/)

---

### Post by H.E. Pennypacker on 2006-06-27
[QUOTE=Bou]
Ubuntu Common Hooker ([http://joelbryanonsoftware.blogspot.com/2006/05/5-ubuntu-common-hooker.html](http://joelbryanonsoftware.blogspot.com/2006/05/5-ubuntu-common-hooker.html)) will autoenable Multiverse and install any package you need to view a given file - e.g. if you download a .cbr comix and don't even know which program to install, it will install Comix and launch it.

Ubuntu Home Backup ([http://joelbryanonsoftware.blogspot.com/2006/05/3-ubuntu-home-backup.html](http://joelbryanonsoftware.blogspot.com/2006/05/3-ubuntu-home-backup.html)) is the app I've been searching for so long. It allows to easily backup your files and settings to any media you choose - including removable media.
[/QUOTE]

Joelbryan is an excellent programmer.  Thank God for him.  

Check out [http://www.ubuntuforums.org/showthread.php?t=204101&highlight=ubuntu+common+hooker](http://www.ubuntuforums.org/showthread.php?t=204101&highlight=ubuntu+common+hooker) for more on Ubuntu Common Hooker.  It may be something that will be implemented in Edgy, if we push the story, and create a buzz.  

Ubuntu Home Backup sounds like a great idea, and I am surprised it doesn't already exist.

---

### Post by cward002 on 2006-08-28
to simplyw00x:

it appears that the link you gave to the .deb for Ubuntu Home Backup is no longer functioning.

---

### Post by toasted on 2006-08-29
Yea thats too bad, any way to find it again?

---

