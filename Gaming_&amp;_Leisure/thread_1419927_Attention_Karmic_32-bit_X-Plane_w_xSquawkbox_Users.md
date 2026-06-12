---
title: "Attention Karmic 32-bit X-Plane w/ xSquawkbox Users!"
date: 2010-03-02
forum: Gaming &amp; Leisure
---

### Post by ptn107 on 2010-03-02
Attention Karmic 32-bit X-Plane w/ xSquawkbox Users!

I was able to restore sound in X-Plane by repackaging a newer openal-soft. It can be downloaded here: _[http://download54.mediafire.com/ei3mmcf1qzkg/imxdiifommn/libopenal1_1.11.753-1_i386.deb]("http://download54.mediafire.com/ei3mmcf1qzkg/imxdiifommn/libopenal1_1.11.753-1_i386.deb")_

This file will upgrade your '/usr/lib/libopenal.so.1.8.466' to '/usr/lib/libopenal.so.1.11.753'.  Install the .deb and create a symlink that X-Plane can see as follows:

```
sudo dpkg -i libopenal1_1.11.753-1_i386.deb
sudo ln -s /usr/lib/libopenal.so.1.11.753 /usr/lib/libopenal.so.0
```

Launch X-Plane normally.

Sorry 64-bit users.  I don't yet have time to recompile ia32-libs with this new version.  Ubuntu 10.04 LTS will include this version for both 32 and 64-bit users.

---

