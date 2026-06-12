---
title: "Enemy Territory"
date: 2006-06-22
forum: Gaming &amp; Leisure
---

### Post by persoontje on 2006-06-22
Hey,

I've been searching but for a while, but I cant find a (working) download for Enemy Territory. Do you know where I can find it (and the patch to 2.6)

I have one version but that gives this error:
```

didier@ice-kubuntu:~/Desktop/et$ ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/tmp/selfgz9897/setup.sh: line 143: 10001 Segmentatie fout        "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting


```

---

### Post by x64Jimbo on 2006-06-22
Well, it says "Verifying archive integrity...all good" which tells me that your download wasn't corrupt or anything. try running it like this:
sudo ./et-linux-2.55.x86.run
You may also want to make sure you've got the latest version of glibc from your repositories.

---

