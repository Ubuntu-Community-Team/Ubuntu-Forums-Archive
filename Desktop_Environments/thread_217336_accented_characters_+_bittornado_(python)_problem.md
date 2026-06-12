---
title: "accented characters + bittornado (python?) problem"
date: 2006-07-17
forum: Desktop Environments
---

### Post by LordMau on 2006-07-17
Hi I've tried to wade thru posts here regarding what I think is a common problem in python programs with regards to accented characters. I've seen complaints in Exaile, Smeg, and in my own personal experience bittornado.

In my case this arises when I download torrents that have filenames with accented letters (ex. Façade). I get this error everytime:

************
BitTorrent T-0.3.13 (BitTornado)
OS: linux2
Python version: 2.4.3 (#2, Apr 27 2006, 14:43:58) 
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)]
wxWindows version: 2.6.1.2pre

Traceback (most recent call last):
  File "/usr/bin/btdownloadgui", line 476, in onInvoke
    apply(event.func, event.args, event.kwargs)
  File "/usr/bin/btdownloadgui", line 2027, in onChooseFile
    self.onChooseFileDone(default, size)
  File "/usr/bin/btdownloadgui", line 2037, in onChooseFileDone
    self.fileNameText.SetLabel('%s' % (lname))
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 10839, in SetLabel
    return _core_.Control_SetLabel(*args, **kwargs)
UnicodeDecodeError: 'utf8' codec can't decode byte 0xa9 in position 16: nexpected code byte
************

Hope someone has a definitive solution on this. What should be done to prevent this? Thanks!

---

### Post by wangbin on 2006-07-17
you could create a python file called sitecustomzie.py under /usr/lib/python2.4/site-packages/

import sys
sys.setdefaultencoding('latin-1')

---

### Post by LordMau on 2006-07-17
I'm sorry don't follow, how'd i use that file with bittornado?
Thanks.

---

### Post by wangbin on 2006-07-18
I met the same error when i using django(a python based web framework) try to output some chinese characters. python try to decode the characters into ascii(the default encoding), which cause that error, when i set the python's default encoding to latin-1, and the  error disappeared.

Hope this will help.

---

### Post by asplode on 2006-07-18
> **LordMau said:**
> I'm sorry don't follow, how'd i use that file with bittornado?
Thanks.

```
sudo gedit /usr/lib/python2.4/site-packages/sitecustomize.py
```
and fill it with
```
import sys
sys.setdefaultencoding('latin-1')
```
and then save it.  presto!

---

### Post by LordMau on 2006-07-18
Ok, I assume that when i start bittorndado that sitecustomize.py will be atuomatically called right? Will try it.

***trying out***

Well the old error's gone but now I have a new one, i've attached it for reference.

Hmmm now what's happening?

---

### Post by asplode on 2006-07-18
> **LordMau said:**
> Ok, I assume that when i start bittorndado that sitecustomize.py will be atuomatically called right? Will try it.

***trying out***

Well the old error's gone but now I have a new one, i've attached it for reference.

Hmmm now what's happening?

looks like its having trouble writing to whatever you're copying it to.  Try downloading it to a different drive/partition, such as your home directory, to see if that works.

---

### Post by LordMau on 2006-07-19
asplode, wangbin, thanks for your help, your tips definitely worked.

My last error was regarding permissions right? Must study up on that!

Thanks so much.

---

### Post by asplode on 2006-07-19
> **LordMau said:**
> asplode, wangbin, thanks for your help, your tips definitely worked.

My last error was regarding permissions right? Must study up on that!

Thanks so much.

Perhaps permissions, or trying to write to an NTFS partition, or a partitions thats not mounted the correct way.  If it works downloading to your home directory, then all is okay, and its the permissions with the partitions.

---

### Post by LordMau on 2006-07-21
Apologies if this is a bit off the subject, but there 2 new issues after the above:

1. The file that was now downloaded, say **"Façade"** comes out in all other apps as **"Fa??ade"**, the accented char does not show properly.

2. When I try to open the file under Comix, another python apps, the following error comes up:
```

Traceback (most recent call last):
  File "/usr/bin/comix", line 5582, in ?
    Comic()
  File "/usr/bin/comix", line 5326, in __init__
    self.load_file(path, -2)
  File "/usr/bin/comix", line 4077, in load_file
    self.refresh_image()
  File "/usr/bin/comix", line 4399, in refresh_image
    ' / ' + str(len(self.file)) + ']', sys.getfilesystemencoding()))
  File "/usr/lib/python2.4/encodings/utf_8.py", line 16, in decode
    return codecs.utf_8_decode(input, errors, True)
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 35-37: invalid data

```

Seems that the sitecustomize.py doesn't get called here.

Any thoughts on how to show these characters propoerly and get opened?

---

