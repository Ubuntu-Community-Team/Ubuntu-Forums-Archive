---
title: "Why has Ubuntu much fewer packages in Sources.gz and Packages.gz than Debian?"
date: 2023-11-04
forum: Debian
---

### Post by ruwolf on 2023-11-04
Hello.

In Ubuntu repositories, there are files like:
[archive.ubuntu.com/ubuntu/dists/mantic/main/source/Sources.xz]("http://archive.ubuntu.com/ubuntu/dists/mantic/main/source/Sources.xz")
[archive.ubuntu.com/ubuntu/dists/mantic/multiverse/source/Sources.xz]("http://archive.ubuntu.com/ubuntu/dists/mantic/multiverse/source/Sources.xz")
[archive.ubuntu.com/ubuntu/dists/mantic/main/binary-amd64/Packages.xz]("http://archive.ubuntu.com/ubuntu/dists/mantic/main/binary-amd64/Packages.xz")
[archive.ubuntu.com/ubuntu/dists/mantic/multiverse/binary-amd64/Packages.xz]("http://archive.ubuntu.com/ubuntu/dists/mantic/multiverse/binary-amd64/Packages.xz")

In Debian, there are like:
[deb.debian.org/debian/dists/stable/main/source/Sources.xz]("http://deb.debian.org/debian/dists/stable/main/source/Sources.xz")
[deb.debian.org/debian/dists/stable/main/binary-amd64/Packages.xz]("http://deb.debian.org/debian/dists/stable/main/binary-amd64/Packages.xz")

Number of packages:
Ubuntu Sources: 2_917 
Ubuntu Packages: 7_125
Debian Sources: 34_346
Debian Packages:  63_352

Comands for counting after downloading:
```
xzgrep -P "^Package: " Sources* | wc -l
xzgrep -P "^Package: " Packages* | wc -l
```

They are hugge differences in counts. Why? I would expect the numbers to be very similar.

---

### Post by deadflowr on 2023-11-04
Main means something different between what Debian means it for and what Ubuntu means it for.

Debian main are all packages which are fully DFSG compliant within debian.
Debian main is 100% free software, with no non-free software required to use them.

Ubuntu's main are simply all open-source packages directly supported by Canonical.


A better comparison would be between Debian main and Ubuntu universe packages.
Since the bulk of Debian's main repository is pulled to populate Ubuntu's universe repository. 


A quick break down of Debian's archives and Ubuntu's archives

Debian:
Main = Fully compliant to the Debian free software guidelines
Contrib = Mostly compliant with Debian's DFSG but require sources outside of main.
Non-free = speaks for itself, as these are not free software.

Ubuntu:
Main = free and open source packages supported directly by Canonical
Universe = Free and open source software supported by the Ubuntu community
Multiverse = not quite open source software
Restricted = non-free software


fwiw:
Multiverse is probably Ubuntu's more complicated repository as it contains software which may be free software,
but is usually either
1) not legal to use everywhere.
2) might have restricted copyrights

Quick References:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
[https://wiki.debian.org/SourcesList#Component]("https://wiki.debian.org/SourcesList#Component")


Ah, there's probably better ways to explain it.

---

### Post by ruwolf on 2023-11-04
Thank you for your explanation, but I still do not understand, because I counted Ubuntu's main and multiverse together.
Because I think, that libre software is usually protected against transformation to less libre / more proprietary version...

---

### Post by #&amp;thj^% on 2023-11-04
My count is different than yours:
```
Total number of packages on Ubuntu's main repository = 6127
Total number of packages on Ubuntu's universe repository = 64026
Total number of packages on Ubuntu's restricted repository = 784
Total number of packages on Ubuntu's multivrese repository = 1009
Percentage of non-free packages on Ubuntu's repositories= 2.55584223055321939100 %

```

---

### Post by ruwolf on 2023-11-04
Oh, thank you very much, I see it now.
I have not seen universe.
I am very sorry. It was my double mistake...

---

### Post by #&amp;thj^% on 2023-11-04
No worries, and nothing to be sorry over.

---

