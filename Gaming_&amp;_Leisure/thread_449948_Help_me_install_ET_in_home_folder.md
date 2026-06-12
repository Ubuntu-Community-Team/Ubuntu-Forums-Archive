---
title: "Help me install ET in home folder"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by timzak on 2007-05-20
After initially installing ET in the default directory, I read here that it is better to install in home folder.  I read a couple of howtos and help posts here with similar topics, and tried everything that was suggested.  While I finally got it installed in the default directory, I keep getting permission errors when trying to install in home folder.  Here's what I've tried:

```
tim@tim-desktop:~/Desktop$ sudo "./et-linux-2.60.x86.run"
```

```
tim@tim-desktop:~/Desktop$ ./et-linux-2.60.x86.run
```

```
tim@tim-desktop:~/Desktop$ sudo ./et-linux-2.60.x86.run
```

```
tim@tim-desktop:~/Desktop$ sudo sh et-linux-2.60.x86.run
```

I am a newbie, so I got everything above from other threads here (and don't necessarily understand the differences).  Just trying everything I can think of.  All of these get the installer running, but give me permission errors when I change the install directory to my home folder.

Per this message:
[http://ubuntuforums.org/showpost.php?p=538732&postcount=1](http://ubuntuforums.org/showpost.php?p=538732&postcount=1)

I changed my install directories to /home/tim/enemy-territory and /home/tim/bin.  It is at this point that I get permission errors telling me I cannot install to these directories.

Any help appreciated.  Forgive my frustration.  I just wish there was ONE set of installation instructions that worked perfectly.

Thanks.

---

### Post by asipi on 2007-05-22
negative
default install is perfect, only what is recommended: do not play as root, play as your user. it will create the required directories in your home folder in /home/username/.etwolf

---

