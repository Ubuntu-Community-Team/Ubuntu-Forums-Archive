---
title: "fglrx problems"
date: 2005-02-03
forum: Gaming &amp; Leisure
---

### Post by macmasterxiv on 2005-02-03
I seem to be having a shared library problem, because of two things.

Running UT2004 returns this:
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History:

Exiting due to error

I think this error is occuring because it can't find libGL.so.1 even though it's in /usr/lib.

Running Skype returns this:
error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

I checked this one and the file is clearly in /usr/lib. I checked the LD_LIBRARY_PATH and it was blank, so I exported the various library paths and I still have the same problem. Any ideas?

---

### Post by ZeroVerteX on 2005-04-20
To fix Skype install libqt3c102-mt from synaptic or apt-get. It is describe as follows:

Qt GUI Library (Threaded runtime version), Version 3
This is the Trolltech Qt library, version 3. It's necessary for
applications that link against the libqt-mt.so.3, e.g. all KDE3
applications.

It worked for me. I installed Skype from the .deb file on the site and then installed libqt3c102 and boom I got Skype! skype://zerovertex if you get it running.

Good Luck!

---

