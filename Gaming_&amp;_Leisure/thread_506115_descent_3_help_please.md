---
title: "descent 3 help please"
date: 2007-07-21
forum: Gaming &amp; Leisure
---

### Post by dragonwings on 2007-07-21
loki descent3

when i try to install using sudo sh /media/cdrom0/setup.sh
i get the below  

/media/cdrom0/setup.sh: 9: function: not found
x86

---

### Post by grayhammer on 2007-07-22
To run this you'll probably need to set up an older debian linux release to run it in.  If you're feeling brave there is a how-to at this link:

[https://help.ubuntu.com/community/WoodyInChroot]("https://help.ubuntu.com/community/WoodyInChroot")

You will have to change one part of the how-to.

Where it says:
```
$ sudo debootstrap --arch i386 woody /opt/woody http://http.us.debian.org/debian
```

It should be:
```
$ sudo debootstrap --arch i386 woody /opt/woody http://archive.debian.org/debian-archive
```

If you are feeling even braver you might look here:
[http://ubuntuforums.org/showthread.php?t=24575]("http://ubuntuforums.org/showthread.php?t=24575")

Using these two how-tos I was able to run kohan again.

Good Luck!

---

### Post by Elblondo on 2007-09-04
Hey dragonwings, got it working already??

I did the following:

1. mounting the descent cd1
2. cp everything to /home/name/d3
3. i copied the setup.gtk (from setup.data/bin/x86/glibc2.1)  to  /home/name/d3
4. and made it executable.
5. startup setup.gtk
6. followed instructions and finished install
7. having old-school fun

good luck!

---

### Post by Elblondo on 2007-09-04
you can also look at the: Reports on old Loki games compatibility item. there are some very good post there to help you.

---

### Post by cogadh on 2007-09-04
> **dragonwings said:**
> loki descent3

when i try to install using sudo sh /media/cdrom0/setup.sh
i get the below  

/media/cdrom0/setup.sh: 9: function: not found
x86
You could also use bash instead of sh:
```
sudo bash /media/cdrom0/setup.sh
```

---

### Post by desb01 on 2009-02-14
TY cogadh, it works fine with bash !!!

---

