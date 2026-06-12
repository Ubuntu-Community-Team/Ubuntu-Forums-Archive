---
title: "Fixed problem writing DVDs, but..."
date: 2006-03-19
forum: Desktop Environments
---

### Post by bleucanard on 2006-03-19
I had problems writing DVDs: every burning software I tried (gnomebaker, k3b, nautilus) went as far as 100%, ejected the disk, closed it again, told me it was finished but actually failed to close the disk, making it unusable.

After looking up the forums, I found the solution in this thread:
[http://www.ubuntuforum.org/showthread.php?t=138312]("http://www.ubuntuforum.org/showthread.php?t=138312")

I do have a Pioneer drive and the smptoms are exactly the same.

I downloaded the latest version of cd+rw-tools (6.1) and built it, and now I'm not sure what to do. I copied the compiled files (executables only) to /usr/bin
(where the originals were), and this fixed the problem with nautilus, but k3b complains that it can't find growisofs (I am not that bothered about it, I like the integrated support in Nautilus anyway).

My question is: when you've downloaded a library / program source and rebuilt it, what is the preferred way of "installing" it : can you just copy the binaries in the right place, do you need to build a package and do it via dpkge ?

---

### Post by chuckyp on 2006-03-19
Most source code includes an install configuration so after ./cofigure which sets everything up.  Then "make" which makes the binararies.  then "make install"  which typically will create directories and place the binaries int he appropriate path.

---

