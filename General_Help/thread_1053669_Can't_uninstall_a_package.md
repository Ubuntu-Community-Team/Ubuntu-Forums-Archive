---
title: "Can't uninstall a package"
date: 2009-01-28
forum: General Help
---

### Post by bwaskiew on 2009-01-28
Hello,

I've installed a 3rd party package (aldrin, from [http://www.pohunek.free.fr/aldrin-nightly-builds/ubuntu/intrepid/](http://www.pohunek.free.fr/aldrin-nightly-builds/ubuntu/intrepid/)), and now I can't seem to remove it.

At first, I tried to install it again (because I had forgotten I had installed it... I still don't remember when I did so, but the files are there and the shortcut created and everything). After it didn't show up in any package manager, I downloaded the .deb manually and discovered it is not 64-bit compatible (I'm on 64-bit Intrepid).

Then just tonight I see that the shortcut is there, so I did a 'locate aldrin' and sure enough it found a bunch of files in (what looks like) all the right spots.

Yet, I can't find it on synaptic, or aptitude. If I try 'apt-get remove aldrin' I can tab complete aldrin, but then it fails, saying it can't find the package.

I'm not sure what to do... I don't want to have to uninstall it manually, because I don't know where all the files are, not to mention that is pretty yucky. I'd rather use a package manager to uninstall it.

I've tried to start Aldrin, and this is the output it gives me:

```
brandon@brandon-ubuntu:~/Desktop$ aldrin
searching /usr/lib/python2.5/etc/debugpath.cfg
searching /home/brandon/.aldrin/path.cfg
searching /etc/aldrin/path.cfg
Traceback (most recent call last):
  File "/usr/bin/aldrin", line 20, in <module>
    import aldrin.main
  File "/usr/lib/python2.5/site-packages/aldrin/main.py", line 25, in <module>
    import pathconfig
  File "/usr/lib/python2.5/site-packages/aldrin/pathconfig.py", line 84, in <module>
    path_cfg = PathConfig()
  File "/usr/lib/python2.5/site-packages/aldrin/pathconfig.py", line 59, in __init__
    assert CFG_PATH, "Unable to find path.cfg"
AssertionError: Unable to find path.cfg

```

I know this isn't really a debugging forum, but it does kind of look like it can't find some necessary values/files. Could it be possible that somehow Aldrin is only partially installed? Can that even happen from a .deb file? This is a clean install of 64-bit Intrepid (I didn't update from 8.04 or anything).

Any ideas?

Thanks,
Brandon

EDIT: Attempt to start Aldrin

---

### Post by zvacet on 2009-01-29
```
sudo apt-get --purge remove aldrin
```

---

### Post by bwaskiew on 2009-01-29
Entering that command gives the following output:

```

brandon@brandon-ubuntu:~/Desktop$ sudo apt-get --purge remove aldrin
[sudo] password for brandon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aldrin

```

Is there a way to determine what files are installed from a .deb without actually installing it? If I could go through the list of files and delete them all manually, then delete the shortcuts and icons and such, then that would pretty much be a manual uninstall, which wouldn't be so bad. It isn't like this happens all the time :)

-Brandon

---

### Post by zvacet on 2009-01-30
You can search for package 

```
locate package_name
```

or

```
sudo find / -name package_name
```

---

### Post by bwaskiew on 2009-01-30
Yep, I basically opened the .deb in archive manager and deleted all the files it had installed. Seems to work about the same as uninstalling it through the package manager :)

Thanks,
Brandon

---

### Post by Neural oD on 2009-01-30
try dpkg - as you said u didn't install from apt. read the manual on dpkg - it will tell you how to uninstall

---

