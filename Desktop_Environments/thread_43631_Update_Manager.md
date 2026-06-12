---
title: "Update Manager"
date: 2005-06-22
forum: Desktop Environments
---

### Post by jkrolen5500 on 2005-06-22
use my own kernel because I like to. Therefore I do not want the update manager telling me that I need linux-image-2.6.10-5-386. I have tried putting the following in /etc/apt/preferences:

Package: linux-image
Pin: version 2.6.10-5-386*
Pin-Priority: 1001


That did not work. How do I configure apt to stop harassing me and show a green check showing im up to date?

Secondly I get this error:

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

I added an untrusted site and don't care that it can't be verified. How do I ignore that warning ?

---

### Post by Xian on 2005-06-22
[QUOTE=jkrolen5500]use my own kernel because I like to. Therefore I do not want the update manager telling me that I need linux-image-2.6.10-5-386. I have tried putting the following in /etc/apt/preferences:

Package: linux-image
Pin: version 2.6.10-5-386*
Pin-Priority: 1001


That did not work. How do I configure apt to stop harassing me and show a green check showing im up to date?[/QUOTE]
There are several ways to place a hold on a pkg.
You should just be able to command line it such as this:

**Note: You will need to do this as su, not sudo.*

```
$ su
$ echo "<package> hold" | dpkg --set-selections
```
Then check the status by this command:
```
$ dpkg --get-selections "<package>"
```

If you like the hands-on method this try this option.
```
$ cd /home/username
$ sudo dpkg --get-selections \* > selections.txt
$ gedit /home/username/selections.txt
```
Change the status of the desired package to 'hold' and save the text file.
Now you just need to read in the modified selections.txt file.
Then you can verify the package status.
```
$ sudo dpkg --set-selections < selections.txt
$ dpkg --get-selections "<package>"
```

---

### Post by jkrolen5500 on 2005-06-22
jer@jerlaptop:~$ dpkg --get-selections "linux-image"
linux-image                                     hold



This is what it shows when i type that but it still says 1 update available.  linux-image is still showing as an available update!

---

### Post by Xian on 2005-06-22
No problem. There are other ways.... :)

You'll need to install the wajig package:
```
$ sudo apt-get install wajig
```
Now use that program to place a package on hold in Apt:
```
$ sudo wajig hold <package_name>
```

---

### Post by jkrolen5500 on 2005-06-22
Thank you that worked.

---

### Post by Xian on 2005-06-22
Great. If you ever want to take a package off of the hold status
the command is as below:

```
$ sudo wajig unhold <package_name>
```

---

### Post by dkitty on 2005-06-23
Ooooh! This is very, very handy. Thank you Xian.

---

### Post by awry on 2005-12-07
Hmm... this thread interests me because I am in the same situation.  I need bleeding edge kernel features, so I always compile my own kernel.  I don't want to download or install any updates to apt's kernel packages.

I've tried pinning (which appeared to work at first -- at least it has the desired functionality with apt-get), and now I've tried putting the packages on hold via dpkg.  Either way, the Update Manager still nags me.

I haven't tried wajig yet, and would prefer not to.  As a bit of a purist, I like doing things through their native interfaces rather than using wrappers.  So does anyone know exactly what wajig is doing here, in dpkg/apt terms?  And why apt pinning and dpkg hold status are failing to fix this problem?

Appreciate any knowledge you might have!

---

