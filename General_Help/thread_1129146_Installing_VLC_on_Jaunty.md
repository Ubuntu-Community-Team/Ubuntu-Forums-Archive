---
title: "Installing VLC on Jaunty"
date: 2009-04-18
forum: General Help
---

### Post by Psyche on 2009-04-18
Hello guys,
I'm trygin to install VLC under Jaunty and I get the following error:

```

Err http://ro.archive.ubuntu.com jaunty/multiverse vlc-data 0.9.9a-1ubuntu1
  404 Not Found
Err http://ro.archive.ubuntu.com jaunty/multiverse libvlccore0 0.9.9a-1ubuntu1
  404 Not Found
Err http://ro.archive.ubuntu.com jaunty/multiverse libvlc2 0.9.9a-1ubuntu1
  404 Not Found
Err http://ro.archive.ubuntu.com jaunty/multiverse vlc-nox 0.9.9a-1ubuntu1
  404 Not Found
Err http://ro.archive.ubuntu.com jaunty/multiverse vlc 0.9.9a-1ubuntu1
  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc-data_0.9.9a-1ubuntu1_all.deb  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/libvlccore0_0.9.9a-1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/libvlc2_0.9.9a-1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc-nox_0.9.9a-1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc_0.9.9a-1ubuntu1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I also tried with apt-get update --fix-missing. Any ideeas?
Thanks in advance.

---

### Post by justin_guerin on 2009-04-18
> **Psyche said:**
> Hello guys,
I'm trygin to install VLC under Jaunty and I get the following error:

```

Err http://ro.archive.ubuntu.com jaunty/multiverse vlc-data 0.9.9a-1ubuntu1
  404 Not Found
Err http://ro.archive.ubuntu.com jaunty/multiverse libvlccore0 0.9.9a-1ubuntu1
  404 Not Found
Err http://ro.archive.ubuntu.com jaunty/multiverse libvlc2 0.9.9a-1ubuntu1
  404 Not Found
Err http://ro.archive.ubuntu.com jaunty/multiverse vlc-nox 0.9.9a-1ubuntu1
  404 Not Found
Err http://ro.archive.ubuntu.com jaunty/multiverse vlc 0.9.9a-1ubuntu1
  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc-data_0.9.9a-1ubuntu1_all.deb  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/libvlccore0_0.9.9a-1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/libvlc2_0.9.9a-1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc-nox_0.9.9a-1ubuntu1_i386.deb  404 Not Found
Failed to fetch http://ro.archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc_0.9.9a-1ubuntu1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I also tried with apt-get update --fix-missing. Any ideeas?
Thanks in advance.

Those versions do not exist on that server, so either your package cache is out of date (apt-get update will fix that) or the server's package cache is out of date.  If it's the latter, you'll just have to wait until the server fixes its problem, or change sources.

Well, scratch that.  I just checked the packages.gz file from the server, and it indicates vlc-data should be version 0.9.9.  So this is a server problem that you can't fix.  Your options are 1) wait until the server updates their site, or 2) switch to another server.

---

