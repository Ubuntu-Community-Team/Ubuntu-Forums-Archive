---
title: "Update Manager Errors"
date: 2009-05-30
forum: General Help
---

### Post by spydamans on 2009-05-30
Lately a little caution triangle has been showing up saying that my system is outdated and to use the update manager to update the system, when i do this all my connections seem to fail, these are the errors that i am receiving.

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: Failed to fetch [http://deb.mulx.net/dists/jaunty/Release.gpg](http://deb.mulx.net/dists/jaunty/Release.gpg)  Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://deb.mulx.net/dists/jaunty/main/i18n/Translation-en_US.bz2](http://deb.mulx.net/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'deb.mulx.net'

W: Some index files failed to download, they have been ignored, or old ones used instead


I dont really know how to fix this, any help?

---

### Post by bacardiandwatermelon on 2009-05-30
The search button is a wonderful thing :-)
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key number>[URL="http://ubuntuforums.org/showthread.php?t=1165924"]
[/URL][ ]("http://ubuntuforums.org/showthread.php?t=1165924")
```[URL="http://ubuntuforums.org/showthread.php?t=1165924"]
[/URL]

---

### Post by spydamans on 2009-05-30
Not sure how to use that command doesnt seem to work. Am i missing something?

---

### Post by _Purple_ on 2009-05-30
Replace <key number> with the actual key number.

---

### Post by spydamans on 2009-06-01
_Purple_ thanks for the help that worked. Now i just need to fix these last two errors

W: Failed to fetch [http://deb.mulx.net/dists/jaunty/Release.gpg](http://deb.mulx.net/dists/jaunty/Release.gpg) Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://deb.mulx.net/dists/jaunty/mai...tion-en_US.bz2](http://deb.mulx.net/dists/jaunty/mai...tion-en_US.bz2) Could not resolve 'deb.mulx.net'

---

### Post by _Purple_ on 2009-06-01
Can you post the content of 
```
gedit /etc/apt/sources.list
```

---

### Post by t0p on 2009-06-01
> **spydamans said:**
> _Purple_ thanks for the help that worked. Now i just need to fix these last two errors

W: Failed to fetch [http://deb.mulx.net/dists/jaunty/Release.gpg](http://deb.mulx.net/dists/jaunty/Release.gpg) Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://deb.mulx.net/dists/jaunty/mai...tion-en_US.bz2](http://deb.mulx.net/dists/jaunty/mai...tion-en_US.bz2) Could not resolve 'deb.mulx.net'

Those repos cannot be fetched from because your system cannot resolve the url "deb.mulx.net".  Your system cannot resolve the url because the site [deb.mulx.net]("http://deb.mulx.net") is offline.  You can verify this yourself by pointing your browser at the url [http://deb.mulx.net]("http://deb.mulx.net"). Whether this is a temporary problem or a permanent state of affairs, I cannot tell.  But the problem is at deb.mulx.net's end, not yours.

---

### Post by michy99 on 2009-06-01
Apparently, deb.mulx.net used to be the repository for playonlinux. It has now been moved to deb.playonlinux.com. See this thread:

[http://ubuntuforums.org/showthread.php?p=7327548](http://ubuntuforums.org/showthread.php?p=7327548)

---

