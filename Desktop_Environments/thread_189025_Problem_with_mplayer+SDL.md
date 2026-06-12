---
title: "Problem with mplayer+SDL"
date: 2006-06-04
forum: Desktop Environments
---

### Post by 123dfdfg43 on 2006-06-04
Hi,

I just did the upgrade to Ubuntu 6.06 version, everything seems fine, except **Mplayer**: when I play a video file with SDL driver, I get this error:

```

SDL: setting windowed mode
*** [pp] Allocating mp_image_t, 544x304x12bpp YUV planar, 248064 bytes
XXX initial  v_pts=0.000  a_pos=3377 (0.422)   1 ??% ??% ??,?% 0 6
*** [pp] Allocating mp_image_t, 544x304x12bpp YUV planar, 248064 bytes
*** [vo] Allocating mp_image_t, 544x304x12bpp YUV planar, 248064 bytes
X11 error: BadMatch (invalid parameter attributes)
Type: 0, display: 0x88660e0, resourceid: 1, serial: 18
Error code: 8, request code: 8d, minor code: 13

MPlayer interrupted by signal 6 in module: flip_page

```

What can I do? Is it an actual bug or can I fix it? I do need SDL driver for advanced features.

Bye,
Andrea

---

### Post by 123dfdfg43 on 2006-06-05
[QUOTE=andrea.ballatore]Hi,

I just did the upgrade to Ubuntu 6.06 version, everything seems fine, except **Mplayer**: when I play a video file with SDL driver, I get this error:

```

SDL: setting windowed mode
*** [pp] Allocating mp_image_t, 544x304x12bpp YUV planar, 248064 bytes
XXX initial  v_pts=0.000  a_pos=3377 (0.422)   1 ??% ??% ??,?% 0 6
*** [pp] Allocating mp_image_t, 544x304x12bpp YUV planar, 248064 bytes
*** [vo] Allocating mp_image_t, 544x304x12bpp YUV planar, 248064 bytes
X11 error: BadMatch (invalid parameter attributes)
Type: 0, display: 0x88660e0, resourceid: 1, serial: 18
Error code: 8, request code: 8d, minor code: 13

MPlayer interrupted by signal 6 in module: flip_page

```

What can I do? Is it an actual bug or can I fix it? I do need SDL driver for advanced features.

Bye,
Andrea[/QUOTE]
This problem has been resolved, I don't know why, but now it works.
Here's the **new** **problem:**
[http://ubuntuforums.org/showthread.php?t=189908](http://ubuntuforums.org/showthread.php?t=189908)

---

