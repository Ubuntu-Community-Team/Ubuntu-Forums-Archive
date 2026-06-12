---
title: "Fglrx Problem ?"
date: 2005-01-11
forum: General Help
---

### Post by Ste on 2005-01-11
Only recently discovered this problem, so I'm not sure how far it dates back or what I've done to get it.

Upgrading the fglrx driver might be one but when I revert back to the old warty one I get the same problem.
Occurs whn I try to run fgl_glxgears.
And running glxgears gives low output iirc from my previous scores.

stephen@rfc1918:~ $ fgl_glxgears
Error: couldn't get fbconfig
stephen@rfc1918:~ $ glxgears
314 frames in 6.0 seconds = 52.333 FPS
226 frames in 5.0 seconds = 45.200 FPS
226 frames in 6.0 seconds = 37.667 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
stephen@rfc1918:~ $

I've read up on the couldn't get fbconfig and it says it's a libGL.so error pointing to the old mesa driver but as they've been gone since my first install I'm not sure that they aren't pointing to something else. Very close to a reinstall at this point but I really don't want to.

stephen@rfc1918:~ $ ldd /usr/X11R6/lib/libGL.so
                libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0x400b9000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0x400c6000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x40188000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x40198000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x402cb000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x80000000)
stephen@rfc1918:~ $

Ste.

---

