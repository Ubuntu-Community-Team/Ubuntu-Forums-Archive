---
title: "kzenexplorer dependency problem"
date: 2006-01-01
forum: General Help
---

### Post by Pawel Stolowski on 2006-01-01
Hi! I'd like to install kzenexplorer0.6.0-ubuntu1 package, but seems it has broken dependency; synaptic claims libnjb4 is required by not installable. There are libnjb1 and libnjb5 packages available, but not libnjb4.... Is there anyway to overcome this problem? Maybe I could create libnjb4 deb myself (how?) or install libnjb5 + libnjb-dev and crete kzenexplorer deb (again, how?). Do deb-realted utilities provide any help for this given these packages already exist but have broken dependency?

---

### Post by MartinJ on 2006-01-04
I'm also trying to get this to work.  I can confirm that kzenexplorer will not install from the repositories.

As Pawel said, libnjb4 is missing, libnjb1 and 5 are available.  Someone mentioned on a slightly related problem (can't find link) that a symlink would be able to direct kzenexplorer to libnjb5 instead of 4.  Is this possible?  I'm fairly new to this so not sure at all how to do it.

---

### Post by Pawel Stolowski on 2006-01-04
I just found the solution. You may recompile the source deb of kzenexplorer - here is a quick howto:
1. install libnjb5 and libnjb-dev: apt-get install libnjb5 libnjb-dev
2. install other build dependencies: apt-get build-dep kzenexplorer
3. also install libattr1-dev and libacl1-dev (for some reason they are needed when compiling but not automatically installed by apt-get)
4. get the source package: apt-get source kzenexplorer
5. go to kzenexplorer-0.6 directory and type: dpkg-buildpackage -rfakeroot -b

It should start compiling; after that you will find ready to install kzenexplorer_0.6-0ubuntu1_i386.deb ;) 

The only problem with this package is the broken menu entry - it appeared in Lost&Found menu, so you need to manually move this entry to Multimedia section.

---

