---
title: "Sage 5.0 in Ubuntu 12.04"
date: 2012-05-16
forum: Education &amp; Science
---

### Post by PGScooter on 2012-05-16
Has anyone installed sage 5.0 (just released two days ago) in Ubuntu 12.04? Did you install from source? If so, did you have to do any workarounds or install unexpected packages?

---

### Post by rtalcott on 2012-05-16
Downloading now the 10.04 version of 5...hopefully it will install...there was a thread here about getting 4.7 running...may need to look at that.
rt

---

### Post by PGScooter on 2012-05-16
Note that there is also a PPA which built for 10.04 but packaged for 12.04. The PPA is here:
[https://launchpad.net/~aims/+archive/sagemath](https://launchpad.net/~aims/+archive/sagemath)
and the discussion is here:
[http://groups.google.com/group/sage-devel/browse_thread/thread/a777364348bb173](http://groups.google.com/group/sage-devel/browse_thread/thread/a777364348bb173)

---

### Post by rtalcott on 2012-05-17
Thank you...I'll give the PPA a try!

EDIT: Looks like the PPA is ver 4.8  not 5.0
rt

---

### Post by PGScooter on 2012-05-17
ah, well I just installed it by source and it was the easiest process possible. I just downloaded and did `make` and that was it. I already had the suggested packages installed
[http://boxen.math.washington.edu/home/sagemath/sage-mirror/src/README.txt](http://boxen.math.washington.edu/home/sagemath/sage-mirror/src/README.txt)
need:
Linux: gcc, make, m4, perl, ranlib, and tar.
   (install these using your package manager)
   On recent Debian or Ubuntu systems (in particular Ubuntu 12.04
   "Precise"), you need the dpkg-dev package.

Note that I did not need the libssl package that the other thread suggested.

The entire make took 4 hours for me. I did a `make test` afterword and that took another hour. All of the tests passed.

Let me know what ends up working for you.

---

### Post by rtalcott on 2012-05-21
PPA now has 5.0 for 12.04
[https://launchpad.net/~aims/+archive/sagemath](https://launchpad.net/~aims/+archive/sagemath)
rt

---

### Post by PC_load_letter on 2012-05-23
It'll be great if someone confirm that 3D plots work well with Open JDK or if it requires JAVA.

---

