---
title: "How does one install g++?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by jedsen on 2006-08-07
I'm trying to install g++ through apt-get, and I get these dependency issues:
**g++ -> g++-4.0 -> libstdc++6-4.0-dev -> libc6-dev -> libc6**
And when I try to install libc6-dev, I get:
**libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu6 is to be installed**
And when I try to install libc6:
**libc6 is already the newest version.**

So, how so do I install g++?

---

### Post by Ramses de Norre on 2006-08-07
Have you got only dapper repos? Because I have it installed without any problem.. What's the exact output of ```
sudo aptitude update && sudo aptitude install g++
```

---

### Post by deeek on 2006-08-07
You could try installing the package build-essential to clear up those dependency issues.

---

### Post by jedsen on 2006-08-07
```
# aptitude install g++
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6-dev
The following NEW packages will be automatically installed:
  cpp g++-4.0 gcc libstdc++6-4.0-dev linux-kernel-headers
The following NEW packages will be installed:
  cpp g++ g++-4.0 gcc libstdc++6-4.0-dev linux-kernel-headers
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7640kB of archives. After unpacking 32.2MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu6 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
g++ [Not Installed]
g++-4.0 [Not Installed]
gcc [Not Installed]
libc6-dev [Not Installed]
libstdc++6-4.0-dev [Not Installed]

Score is 35
```

---

### Post by Ramses de Norre on 2006-08-07
What are your repos? The current version of libc6 is 2.3.6-0ubuntu20 but you've got a higher version..

---

### Post by jedsen on 2006-08-07
Oh, crap, you're right (of course). I turned on the edgy repositiories to upgrade to the kernel-image-2.6.17 to get the native bm43xx drivers... no problems so far having just upgraded the kernel and glibc and a few other things. So to solve this problem I turned the edgy repositories back on temporarialy and then installed g++. Things are working fine so far.

Thanks, and please forgive my noobishness.

---

