---
title: "compiling"
date: 2009-04-14
forum: General Help
---

### Post by anv on 2009-04-14
If I have to compile software from source code how do I fill those dependencies which software package normally has, like libtheora,libtheora-dev, libtheora0.

If I use in installation make install or checkinstall those dependencies which other media software ask are not met.

I ask this generally not only in case of libtheora

---

### Post by 3rdalbum on 2009-04-14
If the software that you are compiling requires a version of libtheora that is more recent than in the repositories, then you need to compile a new version of "libtheora". This will also include a new version of "libtheora-dev".

The new libraries won't interfere with the old libraries; the new libraries and the new program will be installed into /usr/local/lib and /usr/local/bin respectively to differentiate these "local copies" with the original copies.

---

### Post by kpkeerthi on 2009-04-14
> **anv said:**
> If I have to compile software from source code how do I fill those dependencies which software package normally has, like libtheora,libtheora-dev, libtheora0.

If I use in installation make install or checkinstall those dependencies which other media software ask are not met.

I ask this generally not only in case of libtheora

To get the build-time dependencies (-dev packages) of a package, say mplayer, you would do:
```
apt-get build-dep mplayer
```

---

