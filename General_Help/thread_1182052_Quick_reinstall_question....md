---
title: "Quick reinstall question..."
date: 2009-06-08
forum: General Help
---

### Post by lariosa42 on 2009-06-08
Hello,

I just reinstalled Ubuntu 9.04 (I had messed it up by having too much fun).  Before I did this, I backed up my entire "/" directory.  The common wisdom seems to be, "just replace your /home directory, and everything will be back to normal."  However, I had a bunch of proprietary programs on there (e.g. Mathematica) that I would rather not have to install again.

Is there a way to reinstall my old programs by just coping files from the old "/" sub-directories?  If so, which directories should I copy, and how should I set the permission!

Thanks!

Edit: [This]("http://ubuntuforums.org/showthread.php?t=619871&highlight=reinstall") thread had some suggestions, but not quite a full answer.

---

### Post by s3MA00RRNY on 2009-06-08
For proprietary/non-repository programs, make sure you have those debs handy. Maybe dpkg has a cache though? Apt's is in /var/cache/apt/archives. For in-repository programs, Just make sure you have a markings list handy.

Too much fun? :D I had [the same problem]("http://ubuntuforums.org/showthread.php?t=1170757"). I knew that it would be easier if I had installed from repos, so I always looked for them, so that way, I could easily rebuild my system.

---

### Post by lariosa42 on 2009-06-08
Thanks for your help!

Now, I'm having some permissions problems, but I'll post those on [another thread]("http://ubuntuforums.org/showthread.php?p=7424106#post7424106").

---

### Post by s3MA00RRNY on 2009-06-09
So did it work? What did you do to solve the problem?

---

