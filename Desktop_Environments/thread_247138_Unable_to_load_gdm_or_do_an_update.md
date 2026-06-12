---
title: "Unable to load gdm or do an update"
date: 2006-08-30
forum: Desktop Environments
---

### Post by linux_newbie on 2006-08-30
Hi,

For a past couple of days whenever I boot ubuntu dapper, it get stuck when it comes to loading gdm. I could see a watch cursor sitting there for hours but it does not go further. 

I tried booting in the recovery mode and manually typed startx or gdm but still the same issue. Finally I tried kdm since I have kubuntu installed too. Kdm works fine with out any issues.

I am sure that I did not change anything on the system before I started seeing this problem.

Also when I do an update using synaptic in kubuntu, this is what I get:
```

http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.bz2: Sub-process bzip2 returned an error code (127)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.bz2: Sub-process bzip2 returned an error code (127)

```

And these are the problems with it
```

W: GPG error: http://us.archive.ubuntu.com dapper Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv

```

Also when i tried executing bzip2 from the terminal I am getting this:
```

bzip2: error while loading shared libraries: /lib/libbz2.so.1.0: invalid ELF hea der

```

I would appreciate if any tells me what is wrong with my machine ? I like Gnome desktop (nothing against KDE).

I am running ubuntu dapper 2.6.15-26-386 on my dell inspiron 600m.

I can provide more information as needed.

Thanks

---

### Post by stormblue on 2006-08-30
I am having the same update issue.  I do a fresh server install on a compaq m300 and it seems to be a problem.  I have no gui installed.  Any ideas?

---

### Post by dangermouse28 on 2006-08-31
Just to say I have the same problem - updated my laptop last night. Rebooted this morning, get past logging in and am presented with a blank screen and a cursor. Seems like the last update broke Gnome - bugger.

---

### Post by linux_newbie on 2006-09-07
The problem with synaptic is fixed after I followed this
[http://ubuntuforums.org/showthread.php?t=239238](http://ubuntuforums.org/showthread.php?t=239238)

But I still have problems loading Gnome. It just stands there with hourglass cursor. 

Also now I have a crappy font rendering.

I would be very happy if a some ubuntu guru helps me out.

Thanks

---

