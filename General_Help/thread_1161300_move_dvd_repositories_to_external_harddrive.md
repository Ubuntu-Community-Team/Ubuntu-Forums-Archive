---
title: "move dvd repositories to external harddrive"
date: 2009-05-16
forum: General Help
---

### Post by countingbricks on 2009-05-16
I have the Ubuntu 9.04 repositories on DVDs I think they where made using aptoncd. I copied to files on the DVDs to separate folders on a external harddrive and added 

```
deb file:///media/Removable/ISO/Linux/Repositories/ubuntu_904_repositories_1-6/ jaunty main multiverse restricted universe
deb file:///media/Removable/ISO/Linux/Repositories/ubuntu_904_repositories_2-6/ jaunty main multiverse restricted universe
deb file:///media/Removable/ISO/Linux/Repositories/ubuntu_904_repositories_3-6/ jaunty main multiverse restricted universe
deb file:///media/Removable/ISO/Linux/Repositories/ubuntu_904_repositories_4-6/ jaunty main multiverse restricted universe
deb file:///media/Removable/ISO/Linux/Repositories/ubuntu_904_repositories_5-6/ jaunty main multiverse restricted universe
deb file:///media/Removable/ISO/Linux/Repositories/ubuntu_904_repositories_6-6/ jaunty main multiverse restricted universe

```
to the sources.list but when I do a apt-get update  it ignores it

What am i doing wrong?

new info: If I comment out the on-line repository it works but then i can download updates.

---

