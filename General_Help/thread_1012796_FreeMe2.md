---
title: "FreeMe2"
date: 2008-12-16
forum: General Help
---

### Post by kalaka on 2008-12-16
Hi. I'm trying to install a program called FreeMe2. I've tried building it from [source]("http://sourceforge.net/projects/freeme2") but failed. I found [the package on launchpad]("https://launchpad.net/~skoruppa/+archive") so I added the following to my software source list (apt sources.list):
> deb [http://ppa.launchpad.net/skoruppa/ubuntu](http://ppa.launchpad.net/skoruppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/skoruppa/ubuntu](http://ppa.launchpad.net/skoruppa/ubuntu) hardy main
I can install the freeme2 package but I can't use the program! freeme2 and FreeMe2 commands return "command not found" and ```
which freeme2
``` yields no results.

Thanks a lot in advance guys

---

### Post by adult swim on 2008-12-16
i dont think that freeme2 has a gui.  from the readme in the source it says to run it like so

Example configurations:
Decrypt file;
./FreeMe2 some_file
Decrypt file in verbose mode;
./FreeMe2 -v some_file
Decrypt file but force program to ask for sid;
./FreeMe2 -s some_file
Decrypt file but force program to ask for sid in verbose mode;
./FreeMe2 -vs some_file
Decrypt file but force program to ask for sid in verbose mode using FreeMe2 decryption engine.
./FreeMe2 -vs2 some_file

---

### Post by kalaka on 2008-12-17
Yes, I understand that there is no GUI. However, I can't find the "FreeMe2" file that I'm supposed to execute...

---

### Post by fonggiding on 2009-06-25
Has anyone figured this out? My /var/lib/dpkg/info/freeme2.list says
/.
/usr
/usr/bin
/usr/share
/usr/share/doc
/usr/share/doc/freeme2
/usr/share/doc/freeme2/README
/usr/share/doc/freeme2/README.Debian
/usr/share/doc/freeme2/TODO
/usr/share/doc/freeme2/copyright
/usr/share/doc/freeme2/changelog.gz
/usr/share/doc/freeme2/changelog.Debian.gz

and locate doesn't find it either. What am I missing. As of this post, more than 700 people have view this post... Please, if you know anything:(

---

