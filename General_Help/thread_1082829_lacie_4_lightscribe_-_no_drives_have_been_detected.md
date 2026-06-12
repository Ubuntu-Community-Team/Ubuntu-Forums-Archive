---
title: "lacie 4 lightscribe - no drives have been detected - 8.10"
date: 2009-02-28
forum: General Help
---

### Post by DoxSearch on 2009-02-28
Ok so I am running 8.10. The Simplelaber detects my drive, and works burns the images. I can not for the life of me get lacie 4 to see any drives, any ideas? I have searched google up and down, and found nothing matching my issue.

When I got to "print" it shows no drives have been detected

---

### Post by DoxSearch on 2009-02-28
I am getting this error

/usr/4L$ sudo 4L-gui
4L-cli: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


I try installed libstdc++ but get
sudo apt-get install libstdc++6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by DoxSearch on 2009-02-28
someone off irc got it working for me, libstdc++5 needed to be installed, i had libstdc++6

---

