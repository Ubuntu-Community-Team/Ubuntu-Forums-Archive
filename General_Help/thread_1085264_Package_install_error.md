---
title: "Package install error"
date: 2009-03-02
forum: General Help
---

### Post by squawskier on 2009-03-02
Finally have ubuntu up and running!  But now I am getting an error saying there are two broken packages.  Here is the error:
E: /var/cache/apt/archives/libavcodec51_3%3a0.svn20080206-12ubuntu3_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libavcodec.so.51.50.0')

Any Help greatly appreciated!

---

### Post by zvacet on 2009-03-03
```
sudo apt-get -f install
```

---

### Post by squawskier on 2009-03-03
Hey thanks for the help, but I actually figured it out just after posting (I should research more first :s) But now I have a new problem w/ updating packages.  Here is the error:

dpkg: parse error, in file '/var/lib/dpkg/status near line 1286 package 'gdm': value for 'conffiles' has malformatted line '/etc/gdm/modules/accesskeymouseevents'

sorry for what I'm sure are ignorant questions, but I'm new and learning!

---

### Post by squawskier on 2009-03-04
It also says:
E: Sub-process /usr/bin/dpkg returned an error code (2)

any help would be o so greatly appreciatied!

---

