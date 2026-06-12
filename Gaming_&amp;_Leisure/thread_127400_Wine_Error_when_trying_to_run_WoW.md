---
title: "Wine Error when trying to run WoW"
date: 2006-02-08
forum: Gaming &amp; Leisure
---

### Post by Phoenixfatali on 2006-02-08
I'm trying to get World of Warcraft running and had no problems up until trying to get it to run in Wine.  Error messages were
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
FATAL: fglX11CMMFreeSurface: firegl_FreeBuffer() failed!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  546
  Current serial number in output stream:  547

I'm running a laptop with a Radeon 9700 card.  I ran fglrxcfg and glxgears was running without a problem so I don't think it would be the drivers.  I tried the patches from the other thread but they gave me errors when compiling the newest version of Wine and aren't listed to fix this problem.  If anyone is familiar with the freebuffer error it would be much appreciated

---

