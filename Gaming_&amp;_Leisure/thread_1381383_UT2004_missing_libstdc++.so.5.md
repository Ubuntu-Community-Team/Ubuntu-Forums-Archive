---
title: "UT2004 missing libstdc++.so.5"
date: 2010-01-14
forum: Gaming &amp; Leisure
---

### Post by Schui on 2010-01-14
Hello,

I realize this is a super old problem from doing searches. However, the old solutions do not work any more.

My problem is that after installing Unreal Tournament 2004,  I can't run the game because I get this error:
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

When I searched the error in Google I found the old solution:
sudo apt-get install libstdc++5

But this gives me another error:
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source.

What should I do?

Thanks.

Edit:

Super sorry for posting.. I solved it. What I did was find the library online:
[http://packages.ubuntu.com/hardy/i386/libstdc++5/download](http://packages.ubuntu.com/hardy/i386/libstdc++5/download)

The only reason I didn't try this sooner was because I thought it wasn't compatible with my computer. Anyways.. hope this might help someone!

---

