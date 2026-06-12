---
title: "Gmailfs problem"
date: 2006-01-30
forum: Desktop Environments
---

### Post by vvlaw on 2006-01-30
i installed the gmailfs just now...

i think that it was installed.but i can't use it,there are some problem there :

vvlaw@ubuntu:~$ gmailfs.py:Gmailfs:mountpoint: '/home/vvlaw/Desktop/'
gmailfs.py:Gmailfs:unnamed mount options: ['rw']
gmailfs.py:Gmailfs:named mount options: {'username': 'cpn.vvlaw@gmail.com', 'password': 'xxx', 'fsname': 'blah'}
No messages found
HTTP Error 404: Not Found
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 201, in _sendMessage
    if ga.sendMessage(gmsg):
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 594, in sendMessage
    items = self._parsePage(req)
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 352, in _parsePage
    items = _parsePage(self._retrievePage(urlOrRequest))
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 92, in _parsePage
    lines = pageContent.splitlines()
AttributeError: 'NoneType' object has no attribute 'splitlines'
HTTP Error 404: Not Found
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 201, in _sendMessage
    if ga.sendMessage(gmsg):
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 594, in sendMessage
    items = self._parsePage(req)
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 352, in _parsePage
    items = _parsePage(self._retrievePage(urlOrRequest))
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 92, in _parsePage
    lines = pageContent.splitlines()
AttributeError: 'NoneType' object has no attribute 'splitlines'
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 249, in __init__
    matchInode = m.group(2)
AttributeError: 'NoneType' object has no attribute 'group'

~~~

anybody knows that what's wrong with it?

thanks 

vvlaw

---

### Post by lol on 2006-02-01
I have exactly the same problem, using python-libgmail 0.1.3.3 and gmailfs 0.6. I already spent too much time trying to solve this without any success. I guess I will just give up until the next release :(

---

### Post by vvlaw on 2006-02-04
is this the verison problem?

the software own problem?:(

---

