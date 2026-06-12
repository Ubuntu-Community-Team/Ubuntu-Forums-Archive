---
title: "Rssdler terminates"
date: 2009-03-01
forum: General Help
---

### Post by CuBone on 2009-03-01
I'm trying to run rssdler on ubuntu server 8.10. It was working like a charm on my previous system running 7.10, but nowdays rssdler crashes all the time. Dows anyone have any idéa whats going on here. Rssdler version is 0.4.0a, and installed as written in [this]("http://code.google.com/p/rssdler/wiki/InstallInstructions") guide

My download.log


```
20090301.13:09 CRITICAL Unexpected Error: Traceback (most recent call last):
  File "/home/martin/.rssdler/rssdler.py", line 2044, in main
    run()
  File "/home/martin/.rssdler/rssdler.py", line 2016, in run
    rssparse(key)
  File "/home/martin/.rssdler/rssdler.py", line 1871, in rssparse
    pr = page.read()
  File "/usr/lib/python2.5/site-packages/mechanize/_response.py", line 179, in read
    self.__cache.write(self.wrapped.read())
  File "/usr/lib/python2.5/socket.py", line 291, in read
    data = self._sock.recv(recv_size)
  File "/usr/lib/python2.5/httplib.py", line 509, in read
    return self._read_chunked(amt)
  File "/usr/lib/python2.5/httplib.py", line 554, in _read_chunked
    value += self._safe_read(amt)
  File "/usr/lib/python2.5/httplib.py", line 602, in _safe_read
    chunk = self.fp.read(min(amt, MAXAMOUNT))
  File "/usr/lib/python2.5/socket.py", line 309, in read
    data = self._sock.recv(recv_size)
error: (104, 'Connection reset by peer')

```

---

