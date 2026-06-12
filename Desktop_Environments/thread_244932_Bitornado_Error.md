---
title: "Bitornado Error"
date: 2006-08-27
forum: Desktop Environments
---

### Post by remoir on 2006-08-27
Hi 

i noticed that Bitornado gives me this error when i try to open up certain torrent that are in chinese.

Is there any way to fix this ?


==========================================

BitTorrent T-0.3.13 (BitTornado)
OS: linux2
Python version: 2.4.3 (#2, Apr 27 2006, 14:43:58) 
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)]
wxWindows version: 2.6.1.2pre

Traceback (most recent call last):
  File "/usr/bin/btdownloadgui", line 2325, in _next
    savedas = dow.saveAs(choosefile, d.newpath)
  File "/usr/lib/python2.4/site-packages/BitTornado/download_bt1.py", line 407, in saveAs
    if path.exists(path.join(file, x['path'][0])):
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'ascii' codec can't decode byte 0xb1 in position 1: ordinal not in range(128)

---

