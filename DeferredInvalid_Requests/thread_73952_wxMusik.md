---
title: "wxMusik"
date: 2005-10-10
forum: Deferred/Invalid Requests
---

### Post by The Hedgehog on 2005-10-10
It would be nice to find wxMusik on a repository. I just tried the Windows version and I liked it very much. I would love to have this on Linux.

---

### Post by LazyP on 2005-11-18
I compiled it myself for linux. Not too much problems once you get all the correct libraries installed, with the right versions.

I could put together my binary and the libraries in a tar-file if someone wants them. Works for sure on both Hoary and Breezy.

---

### Post by pkaeding on 2005-12-28
LazyP--  Did you happen to take notes on what packages you had to install to meet all the dependancies?  I thought I had them all, but then the build failed.

I would appreciate any insight you might have

---

### Post by LazyP on 2005-12-29
[QUOTE=pkaeding]LazyP--  Did you happen to take notes on what packages you had to install to meet all the dependancies?  I thought I had them all, but then the build failed.

I would appreciate any insight you might have[/QUOTE]

No, unfortunately I didn't do that. I just followed the instructions on the wxMusik homepage. Then I fixed some settings when running the ccmake command. Here follows the interactive window from that command after my changes, maybe it can help you?
```

 CMAKE_BACKWARDS_COMPATIBILITY    2.0
 CMAKE_BUILD_TYPE                 RelWithDebInfo
 CMAKE_INSTALL_PREFIX             /usr/local
 EXECUTABLE_OUTPUT_PATH
 FLAC_LIBRARY                     /usr/lib/libFLAC.so
 FMOD_LIBRARY                     /usr/local/lib/libfmod-3.74.1.so
 LIBRARY_OUTPUT_PATH
 MAC_LIBRARY                      MAC_LIBRARY-NOTFOUND
 MUSEPACK_LIBRARY                 /usr/lib/libmpcdec.so
 OPTION_SUPPORT_APE               OFF
 OPTION_SUPPORT_FLAC              ON
 OPTION_SUPPORT_MPC               ON
 SQLITE_LIBRARY                   /usr/lib/libsqlite.so
 WXWINDOWS_USE_DEBUG_LIBS         ON
 WXWINDOWS_USE_SHARED_LIBS        ON
 WXWINDOWS_USE_UNICODE            ON

```

---

### Post by jdong on 2006-01-02
Not in Dapper. Please read policy before requesting.

---

