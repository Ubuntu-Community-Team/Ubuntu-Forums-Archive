---
title: "Xubuntu minimal?"
date: 2018-04-28
forum: Desktop Environments
---

### Post by xubu2 on 2018-04-28
Since there's no option for a minimal install for xubuntu i've used the netboot installer in the past to install 16.04.
But the netboot installer for 18.04 is still in beta.
Does anybody know when it's finished ?

---

### Post by Bashing-om on 2018-04-28
xubu2; Hello

See:
[http://xubuntu.org/news/introducing-xubuntu-core/](http://xubuntu.org/news/introducing-xubuntu-core/)

-'buntu; just do it-

---

### Post by sudodus on 2018-04-28
There are released netboot images for 18.04 LTS. See this link, [http://cdimages.ubuntu.com/netboot/](http://cdimages.ubuntu.com/netboot/)

You can also get Xubuntu Core directly as an iso file or via torrent from a Xubuntu team member, [https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

---

### Post by xubu2 on 2018-04-28
Thanks for the quick reply.
Guess i'll have to wait till it's out of beta.
Cheers.

---

### Post by sudodus on 2018-04-28
It **is released** (no longer beta).

Edit:
```

$ <<<'d751ad8cde5876018ddc39c964c236c0  xubuntu-18.04-core-amd64.iso' md5sum -c
xubuntu-18.04-core-amd64.iso: OK

```

---

### Post by xubu2 on 2018-04-29
[http://cdimage.ubuntu.com/netboot/18.04/?_ga=2.23576122.1298492963.1525006009-2012454260.1525006009](http://cdimage.ubuntu.com/netboot/18.04/?_ga=2.23576122.1298492963.1525006009-2012454260.1525006009)
This isn't changed yet?

---

### Post by sudodus on 2018-04-29
No but it is accepted "ready" as Bionic Final and archived as you can see in this link:

[Bionic Final (archived)](http://iso.qa.ubuntu.com/qatracker/milestones/389/builds)

As you can see, it is version '20101020ubuntu543' (and it is the current one).

According to [iso.qa.ubuntu.com/qatracker/milestones/389/builds/171036/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/389/builds/171036/testcases)

> Notice board

debian-installer netboot builds.
These are reset every time a new debian-installer is uploaded and not on a daily basis.



Looking into details:

```

Index of /ubuntu/dists/bionic/main/installer-amd64/[COLOR="#cc0000"]20101020ubuntu543[/COLOR]/images/netboot
[ICO]NameLast modifiedSize
[PARENTDIR]Parent Directory -
[ ]boot.img.gz2018-04-25 21:23 52M
[ ]ldlinux.c322018-04-25 21:23 113K
[ ]mini.iso2018-04-25 21:23 64M
[ ]netboot.tar.gz2018-04-25 21:23 52M
[ ]pxelinux.02018-04-25 21:23 41K
[DIR]pxelinux.cfg/2018-04-25 21:23 -
[DIR]ubuntu-installer/2018-04-25 21:23 -
[DIR]xen/2018-04-25 21:23 - 

Index of /ubuntu/dists/bionic/main/installer-amd64/[COLOR="#0000CD"]current[/COLOR]/images/netboot
[ICO]NameLast modifiedSize
[PARENTDIR]Parent Directory -
[ ]boot.img.gz2018-04-25 21:23 52M
[ ]ldlinux.c322018-04-25 21:23 113K
[ ]mini.iso2018-04-25 21:23 64M
[ ]netboot.tar.gz2018-04-25 21:23 52M
[ ]pxelinux.02018-04-25 21:23 41K
[DIR]pxelinux.cfg/2018-04-25 21:23 -
[DIR]ubuntu-installer/2018-04-25 21:23 -
[DIR]xen/2018-04-25 21:23 -


```

---

### Post by xubu2 on 2018-04-29
Okay.
Thanks for the help.
Gonna give it a go later this week.
Cheers.

---

### Post by sudodus on 2018-04-29
You are welcome and good luck :-)

---

### Post by xubu2 on 2018-05-05
Just finished installing xubuntu minimal with the net-installer and everything went smooth!
Great work & thanks.

---

