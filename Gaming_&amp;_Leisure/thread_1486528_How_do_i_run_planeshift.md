---
title: "How do i run planeshift"
date: 2010-05-17
forum: Gaming &amp; Leisure
---

### Post by Zireth ZH on 2010-05-17
I installed the game .. i try to run the game but nothing happends

---

### Post by Carpentr on 2010-05-17
```

cd /[file location]
sudo ./[planeshift file name]

```

That worked for me when I installed it a few months ago. Don't forget to replace the [] with the correct location and file name.

---

### Post by Zireth ZH on 2010-05-18
This is what i did to install... and then run:

hilderith@hilderith-desktop:~$ cd /home/hilderith/Downloads
hilderith@hilderith-desktop:~/Downloads$ sudo chmod +x PlaneShift-v0.5.3-x86.binhilderith@hilderith-desktop:~/Downloads$ ./PlaneShift-v0.5.3-x86.bin

(main.tcl:4403): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
hilderith@hilderith-desktop:~/Downloads$ cd /home/hilderith/Downloads/PlaneShifthilderith@hilderith-desktop:~/Downloads/PlaneShift$ sudo ./psclient
Inconsistency detected by ld.so: dl-close.c: 731: _dl_close: Assertion `map->l_init_called' failed!

---

### Post by Carpentr on 2010-05-18
I'm no expert, but you might want to take a look at the following links because they seem to be where your errors are occurring:

[http://library.gnome.org/devel/gdk/]("http://library.gnome.org/devel/gdk/")

[http://www.unixguide.net/linux/faq/05.05.shtml]("http://www.unixguide.net/linux/faq/05.05.shtml")

You could try updating them to the newest version. Maybe you're missing a required library?

Planeshift requires the following:

> Linux (2.6.27+ kernel, glibc 2.9)

Try installing the glibc package,

```
sudo apt-get install glibc-2.10-1
```

That's an older version and it probably won't work though. You could try doing that. Or with a little extra effort you could get the updated version of the package(2.9 is required by Planeshift) from launchpad.

[https://launchpad.net/ubuntu/+source/glibc]("https://launchpad.net/ubuntu/+source/glibc")

EDIT: The most recent version is found here:
[https://launchpad.net/ubuntu/+source/glibc/2.9-4ubuntu6.1]("https://launchpad.net/ubuntu/+source/glibc/2.9-4ubuntu6.1")

---

