---
title: "DWL 520 help"
date: 2005-05-11
forum: Desktop Environments
---

### Post by birv2 on 2005-05-11
Hi all,

I'm desperately trying to get my wireless pci card working under Kubuntu (on about my 10 distro and would like to make this one work).  I'm following the article in the wiki at [http://www.ubuntulinux.org/wiki/DLinkDWL520E1](http://www.ubuntulinux.org/wiki/DLinkDWL520E1) .

Anyway, I am down to #4 on Installing the Hostap Kernel Module, but when I try to tar the file, I get these three errors:
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Errr exit delayed from previous errors.

I'm not a total newbie, but I'm no linux guru.  I rechecked my entry of the previous commands and I didn't make any errors as far as I can tell.

Any help would be greatly appreciated!
Bob in PA ](*,)

---

### Post by birv2 on 2005-05-11
And I might also add that I can't add the extra repositories, since I need the wireless to work to get on the internet.  Unless I'm missing something really obvious.
Bob

---

### Post by dbloom on 2005-05-31
this may seem naive and possibly something you've done already, but when i untar files i've always needed to put a hyphen ("-") before the command line arguments.  so instead of 'tar xjvf', try 'tar -xjvf'.  

more specifically, instead of

```
tar xjvf hostap-source.tar.bz2
``` 

use

```
tar -xjvf hostap-source.tar.bz2
``` 

again, i don't know if it works without the hyphen (i'm at work on winxp so i can't test it out), but that was the first thing i noticed...  good luck.

oh, also, since you're out of your home directory, you may need to use sudo.

ie,
```
sudo tar -xjvf hostap-source.tar.bz2
```

---

