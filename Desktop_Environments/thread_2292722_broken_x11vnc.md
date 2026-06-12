---
title: "broken x11vnc"
date: 2015-08-30
forum: Desktop Environments
---

### Post by danielsender on 2015-08-30
I had x11vnc running OK on a Dell M4300 with 14.04.3. After an upgrade it doesn't work anymore, it comes back with the message:

```
x11vnc: error while loading shared libraries: libvncclient.so.0: cannot open shared object file: No such file or directory
```

It appears that it should be a member of *libvncserver0 *however if I do "dpkg -L libvncserver0" I get:

```
/./usr
/usr/share
/usr/share/doc
/usr/share/doc/libvncserver0
/usr/share/doc/libvncserver0/changelog.Debian.gz
/usr/share/doc/libvncserver0/copyright
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libvncserver.so.0.0.0
/usr/lib/x86_64-linux-gnu/libvncserver.so.0
```

On another machine also running 14.04.3 I get:

```
/./usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libvncserver.so.0.0.0
/usr/lib/x86_64-linux-gnu/libvncclient.so.0.0.0
/usr/share
/usr/share/doc
/usr/share/doc/libvncserver0
/usr/share/doc/libvncserver0/README.gz
/usr/share/doc/libvncserver0/TODO
/usr/share/doc/libvncserver0/NEWS.gz
/usr/share/doc/libvncserver0/copyright
/usr/share/doc/libvncserver0/changelog.Debian.gz
/usr/lib/x86_64-linux-gnu/libvncclient.so.0
/usr/lib/x86_64-linux-gnu/libvncserver.so.0
```

Does this mean that libvncserver0 is broken or something had changed?

Thanks in advance.

---

### Post by steeldriver on 2015-08-30
Have you tried just re-installing the package?

```

sudo apt-get install --reinstall libvncserver0

```

---

### Post by danielsender on 2015-08-30
Yes, I did but no avail. I just compared the sizes of the previous and current versions and they are significantly different - unless they decided to remove the libvncclient.so.0 from that package and put it somewhere else.

---

### Post by steeldriver on 2015-08-30
What exact version of the package is it? e.g.

```

apt-cache policy libvncserver0

```

---

### Post by danielsender on 2015-08-30
```

libvncserver0:
  Installed: 0.9.9+dfsg-6~ubuntu14.04.1~ppa1
  Candidate: 0.9.9+dfsg-6~ubuntu14.04.1~ppa1
  Version table:
 *** 0.9.9+dfsg-6~ubuntu14.04.1~ppa1 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     0.9.9+dfsg-1ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     0.9.9+dfsg-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

### Post by steeldriver on 2015-08-30
OK so it seems that you have a PPA that is providing a non-standard version of the package: the standard version for Ubuntu 14.04.3 is 

```

~$ apt-cache policy libvncserver0
libvncserver0:
  Installed: 0.9.9+dfsg-1ubuntu1.1
  Candidate: 0.9.9+dfsg-1ubuntu1.1

```

---

### Post by danielsender on 2015-08-30
That's strange, I don't think I set any PPA related to libvncserver0 , do you happen to know who could be doing that?

Thanks.

---

### Post by danielsender on 2015-08-31
Yes, I realised that I entered a ppa (mc3man) for some ffmpeg related program and for some reason he is also providing libvncserver0 - so I just disabled that ppa.

Thank you very much for your time and help.

Cheers,

Daniel

---

### Post by steeldriver on 2015-08-31
OK glad you fixed it - it might be a good idea to submit a bug report to the PPA maintainer mentioning the apparently missing library files

---

### Post by toddk63 on 2015-11-21
I want to say I just had the exact same problem...installing mc3man ffmpeg and x11vnc subsequently breaking after an update.  The solution here worked a treat.  To reiterate...Disable mc3man PPA in Software Center, remove libvncserver0, install libvncserver0.

Is there any other ffmpeg repositories we could have used besides mc3man?

Thanks,

Todd K.

---

