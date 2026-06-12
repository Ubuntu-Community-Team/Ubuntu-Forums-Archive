---
title: "Cannot open package manager or add/remove programs.... weird error message"
date: 2008-12-21
forum: General Help
---

### Post by daemonwebshark on 2008-12-21
Hi, I recently switched to Ubuntu after being extremely frustrated with windows in general and overall I am very pleased.  But lately I have been having some major problems.  I tried to install the package that makes the OSX type dock, and I got several error messages. I just kind of gave up on it, and decided not to worry about it.  But after that happened, I get a persistent error message that won't allow me to go into the add/remove programs at all, or the package manager. here is the message it gives me

E: Type 'sudo' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any ideas? This is very frustrating because I can't really change anything because of it.  Any help will be very much appreciated! Thanks.

---

### Post by SlidingHorn on 2008-12-21
This should help

[http://ubuntuforums.org/showthread.php?t=668421](http://ubuntuforums.org/showthread.php?t=668421)

---

### Post by drs305 on 2008-12-21
Actually it's your sources.list that has an error on line 55.
Backup sources.list and open for editing:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit +55 /etc/apt/sources.list  # the cursor will position itself on line 55

```

If it is the only error in sources.list, you can also just put a comment symbol **#** at the start of the line and it will be ignored and will probably solve your problem:

If the error isn't obvious, post the results.
```

cat /etc/apt/sources.list

```
Once corrected, save the file and run:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by daemonwebshark on 2008-12-21
After I tried the second code you gave me, I got a huge list, but on line 55, i got  "sudo apt-get update"  how in the world could there be an error for that? thanks for the really quick reply!  one of the reasons i love ubuntu is that the community is so willing to help others! it is very much appreciated.

---

### Post by daemonwebshark on 2008-12-21
I just ignored some of the error stuff and followed the rest of the instructions you gave me and the error message went away. THank you so much!

---

