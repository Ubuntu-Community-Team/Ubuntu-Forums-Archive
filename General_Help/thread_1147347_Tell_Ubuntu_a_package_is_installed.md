---
title: "Tell Ubuntu a package is installed"
date: 2009-05-03
forum: General Help
---

### Post by wesg on 2009-05-03
I compiled Mediatomb from the source, but now I want to install the daemon package. Unfortunately, the system is telling me that I can't because Mediatomb-common is not installed. Technically it is, because I compiled it, but the system can't tell.

How can I force Ubuntu into knowing the package is installed and to continue on in this installation?

---

### Post by unutbu on 2009-05-03
I believe the command
```

sudo dpkg -i --force-all PACKAGE.deb
```

will tell dpkg to install PACKAGE.deb regardless of dependency errors.

---

### Post by wesg on 2009-05-03
Thanks, unutbu, that finally got my setup working.

---

### Post by wesg on 2009-05-03
I have another problem now. Whenever I try to use apt-get to install something else, i get a warning that mediatomb-daemon has unmet dependencies. Can I silence this warning and continue installing other stuff?

---

### Post by unutbu on 2009-05-03
Here are some hackish possibilities:
[list]
[*] Remove the mediatomb-daemon package and compile it yourself.
This is clean. No fuss with apt.
[*] Remove the mediatomb-daemon package, extract the control files, remove mediatomb-common from the dependencies, repackage the .deb, then install the doctored deb.
This is dirty. Probably wouldn't survive a package update.
[*] Install mediatomb-common, then run Synaptic, select the mediatomb-common package, Click Package>Lock Version (so apt does not try to update it). Then install your compiled version of mediatomb-common on top of it with something like "sudo make install".
This too feels dirty.
[/list]

I think the first possibility is the best if you can do it.

Also, maybe someone else knows a better way. I'm not all that knowledgable about APT.

---

### Post by wesg on 2009-05-03
I'd like to compile Mediatomb-daemon myself, but it doesn't seem like there is source code available for it alone. It seems to come with the common package as well. Any suggestions as to how I can download the daemon source code?

---

### Post by unutbu on 2009-05-03
Well, it appears mediatomb-daemon is not a compiled program -- it is just a few configuration files: [http://packages.ubuntu.com/jaunty/all/mediatomb-daemon/filelist](http://packages.ubuntu.com/jaunty/all/mediatomb-daemon/filelist)

```
/etc/default/mediatomb
/etc/init.d/mediatomb
/etc/logrotate.d/mediatomb
/etc/mediatomb/config.xml
/usr/share/doc/mediatomb-daemon/README.Debian
/usr/share/doc/mediatomb-daemon/changelog.Debian.gz
/usr/share/doc/mediatomb-daemon/changelog.gz
/usr/share/doc/mediatomb-daemon/copyright
```

You could simply copy each of these files to, say, /tmp, then
```

sudo dpkg -r mediatomb-daemon
```

and the copy the files back to their former locations. 
That way, mediatomb-daemon would not be officially installed, APT will not complain,
and you'll have all the functionality of mediatomb-daemon (but no updates).

---

