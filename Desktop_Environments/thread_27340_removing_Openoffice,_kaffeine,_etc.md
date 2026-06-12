---
title: "removing Openoffice, kaffeine, etc"
date: 2005-04-15
forum: Desktop Environments
---

### Post by roffles on 2005-04-15
Hi all,

I was wondering if anyone knows how to remove openoffice from kubuntu? I am using apt-get remove openoffice but it wants to remove the kubuntu-desktop package as well. This is kind of worrying because I'm afraid a whole bunch of stuff will break if I continue. This also goes for trying to remove kaffeine. I'm not that concerned about kaffeine, but openoffice takes a pretty fair chunk of space and I really hate it  :mad: so I won't be using it anyway. Thanks for any help that you guys can provide.

---

### Post by accuser on 2005-04-15
kubuntu-desktop is a meta package, and as such contains nothing but references to other packages, including openoffice. You can remove kubuntu-desktop to remove openoffice, and it won't cause you too many problems, but be aware that new package dependencies added to kubuntu-desktop will not automatically be installed anymore.

You may want to check these forums for a thread discussing the use of debfoster.

---

