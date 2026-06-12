---
title: "How do I get Enlightenment 16??"
date: 2005-08-15
forum: Desktop Environments
---

### Post by Psquared on 2005-08-15
I thought with just the "universe" enabled I could get it. It shows up in Synaptic, but it won't let me install.

Somebody please share their sources.list that will enable me to download e16.

Thanks

---

### Post by jasmuz on 2005-08-15
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by sb73542 on 2005-08-16
Hmmm, the above list doesn't work for me.  "apt-get install enlightenment" tells me:

Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate


enlightenment-data also also doesn't work.

---

### Post by Psquared on 2005-08-16
[QUOTE=sb73542]Hmmm, the above list doesn't work for me.  "apt-get install enlightenment" tells me:

Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate


enlightenment-data also also doesn't work.[/QUOTE]

Same here. Has E16 been removed?

---

### Post by PMO6022 on 2005-08-16
I don't think E16 has been removed
```
pmorris@ubuntu:~ $ apt-cache policy enlightenment
enlightenment:
  Installed: 1:0.16.6-3ubuntu1
  Candidate: 1:0.16.6-3ubuntu1
  Version table:
 *** 1:0.16.6-3ubuntu1 0
		500 http://archive.ubuntu.com hoary/universe Packages
		100 /var/lib/dpkg/status
```Looks like it is in universe, as Psquared said. I tried installing it, even though I already have it:
```
pmorris@ubuntu:~ $ sudo apt-get install enlightenment
Reading package lists... Done
Building dependency tree... Done
enlightenment is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
So it seems like it is there and installable for me.  I don't know what is going on for you guys. Sorry.

---

### Post by André on 2005-08-17
If you already installed it maybe it´s still on in your /var/cache/apt/archives that´s why it may work.

I am not at home right now and therefore i can´t test it but maybe the package is missing on the server. If the problem doesn´t go away i think you should open bug report.

Greetings
André

---

### Post by j.hill on 2005-08-25
It looks like there are packages available at debian.org.  Would they work on Ubuntu?  (There are versions for all Debian branches.)

---

### Post by André on 2005-08-25
You can test them, but sometimes Debian has different dependencies (like using a newer package). Could be, that you run into problems there. Better would be to open a bug report and use Ubuntu ones.

It should be safe to just try them. If they complain about missing dependencies you should uninstall them and not try to use some other Debian packages for the missing dependencies. But that's just my opinion.

Hope you can solve your problems.

Greetings
André

---

### Post by basttrax on 2005-09-23
Hey everyone,  :) 

I'm having the same problems thats described above.
I did install E17 and then deleted it realizing that I actually wanted E16. I uninstalled E17 through Synaptic. Maybe that has some effect?
Is there a different repository I can add to get it? I googled all night before I found this posting describing the same problem as mine.

Thanks alot,

Basttrax

---

### Post by Hairy_Palms on 2005-09-23
you could see if you can force version on the enlightenment package to 16 rather than 17

---

### Post by basttrax on 2005-09-23
The problem is that E16 dosn't seem to have a version listed. I think thats why I'm getting the error....

---

### Post by Dooglus on 2005-09-23
I'm not sure what the problem is.  The Packages.bz2 file looks OK to me:

```

Package: enlightenment
Priority: optional
Section: universe/x11
Installed-Size: 1180
Maintainer: Laurence J. Lane <ljlane@debian.org>
Architecture: i386
Version: 1:0.16.6-3ubuntu1
Replaces: enlightenment-nosound, enlightenment-sound, enlightenment-dox
Provides: x-window-manager
Depends: enlightenment-data (>= 0.16.5-1), imlib11, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.2.ds1-4), libesd0 (>= 0.2.29-1) | libesd-alsa0 (>= 0.2.29-1), libfnlib0 (>= 0.5-12), libice6 | xlibs (>> 4.1.0), libsm6 | xlibs (>> 4.1.0), libttf2, libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxtst6 | xlibs (>> 4.1.0)
Recommends: esound, menu
Suggests: enlightenment-theme, eterm | x-terminal-emulator, e16keyedit, e16menuedit
Conflicts: dox, enlightenment-dox, enlightenment-docs, menu (<< 2.0), enlightenment-theme (<< 0.16.1-0)
Filename: pool/universe/e/enlightenment/enlightenment_0.16.6-3ubuntu1_i386.deb
Size: 471838
MD5sum: 831ec5efc54209c158fd338efda23024

```

You can check it out for yourself like this:

```

$ wget -o/dev/null -O- http://archive.ubuntu.com:/ubuntu/dists/hoary/universe/binary-i386/Packages.bz2 | bzcat | grep /enlightenment_
Filename: pool/universe/e/enlightenment/enlightenment_0.16.6-3ubuntu1_i386.deb

```

Then you can download the .deb like this:

```

wget http://archive.ubuntu.com:/ubuntu/pool/universe/e/enlightenment/enlightenment_0.16.6-3ubuntu1_i386.deb

```

And install it like this:

```

sudo dpkg -i enlightenment_0.16.6-3ubuntu1_i386.deb

```

Does that work for you?  If not, where does it fail?

If it fails due to a dependancies you could try installing the dependancies first, but if you got this far then what's the problem I wonder...

---

### Post by basttrax on 2005-09-23
basttrax@ubuntu:~ $ wget -o/dev/null -O- [http://archive.ubuntu.com:/ubuntu/dists/hoary/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com:/ubuntu/dists/hoary/universe/binary-i386/Packages.bz2) | bzcat | grep /enlightenment

bzcat: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzcat: Invalid argument
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

This is what I get when i try to check the file.

---

### Post by Dooglus on 2005-09-23
Are you going through a caching proxy server?  If so, perhaps it's caching a broken version of that file.  Try visiting the same URL ( [http://archive.ubuntu.com/ubuntu/d...86/Packages.bz2](http://archive.ubuntu.com/ubuntu/d...86/Packages.bz2) ) in a browser and hitting refresh - that might get the proxy to refresh its broken version.

Notice I left colons after the ".com" in both URLs.  That was a mistake, but wget doesn't seem to mind.  Ignore the colons I put after ".com".

Alternatively, try changing the 'http://' to an 'ftp://' in the commands.  It should work the same, but may get past the problem of the corrupted cache, if indeed that's what it is.

---

### Post by basttrax on 2005-09-23
ok i tried everything with no resolve. i'll print what i get everytime i try to install it, it's the same with apt-get, or symanitic thingy.

basttrax@ubuntu:~ $ sudo apt-get install enlightenment
Reading package lists... Done
Building dependency tree... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate
basttrax@ubuntu:~ $ sudo apt-get install enlightenment-data
Reading package lists... Done
Building dependency tree... Done
Package enlightenment-data is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment-data has no installation candidate

hope this helps a little,
thanks for everyone helping so far, i really do aprechate it.

---

### Post by basttrax on 2005-09-25
anyone have any ideas?

---

### Post by Psquared on 2005-10-03
[QUOTE=basttrax]anyone have any ideas?[/QUOTE]

Nope, same exact problem here. We may have to wait for the breezy repos to be fully populated after the release date.

---

### Post by Samuli on 2005-10-28
The first time I installed enlightenment (not more than hour ago) via apt-get everything was fine, but now I get the exact same error that you do. Odd stuff. Oh, and I didn't change any repositories or anything. 

When I tried to download the .deb file from the servers I got this error: [http://archive.ubuntu.com:/ubuntu/pool/universe/e/enlightenment/enlightenment_0.16.6-3ubuntu1_i386.deb:](http://archive.ubuntu.com:/ubuntu/pool/universe/e/enlightenment/enlightenment_0.16.6-3ubuntu1_i386.deb:) Bad port number.

---

