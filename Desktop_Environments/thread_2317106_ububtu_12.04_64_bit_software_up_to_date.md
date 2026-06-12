---
title: "ububtu 12.04 64 bit software up to date"
date: 2016-03-13
forum: Desktop Environments
---

### Post by rdema19403 on 2016-03-13
i trry to run software up to date and get this message ant ideas how to fix this

W:Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
Thanks in advance Ralph

---

### Post by oldos2er on 2016-03-13
[http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu](http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu)

---

### Post by Dennis N on 2016-03-13
If you are updating Chrome Browser, 64-bit (as you indicate), I found you can just ignore the error. The update will still be done.

---

### Post by deadflowr on 2016-03-13
Google Chrome is no longer supported on Ubuntu 12.04, regardless of whether 32-bit or 64-bit.
So, fixing the broken repository entry will have as much affect as disabling the repository, as there will never be any update that you can use.

---

### Post by oldos2er on 2016-03-13
Thanks for the clarification, deadflowr.

---

### Post by Dennis N on 2016-03-13
Do you know anything of the problem they have with 64-bit Chrome on 64-bit Ubuntu 12.04? Does Chrome now need a more recent kernel to function? The announcement* says nothing about that part.

*[https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/FoE6sL-p6oU](https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/FoE6sL-p6oU)

---

### Post by deadflowr on 2016-03-13
> **Dennis N said:**
> Do you know anything of the problem they have with 64-bit Chrome on 64-bit Ubuntu 12.04? Does Chrome now need a more recent kernel to function? The announcement* says nothing about that part.

*[https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/FoE6sL-p6oU](https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/FoE6sL-p6oU)

I doubt it kernel related, as users could simply install the trusty hwe kernel on precise.
I think it's more that they no longer want to build it against Precise's ancient software.

---

### Post by Dennis N on 2016-03-13
Well, thanks. I didn't know they were dropping all Ubuntu 12.04 support regardless of architecture. I got the error on 64-bit Chrome on 14.04, and as I said, I just ignored it and saw it went through anyway.

---

