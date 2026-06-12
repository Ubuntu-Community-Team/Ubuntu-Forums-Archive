---
title: "gmailfs on Feisty behind proxy"
date: 2007-03-22
forum: Desktop Environments
---

### Post by mosestruong on 2007-03-22
Has anyone been able to get gmailfs working? I'm behind a firewall, and I have entered those details in gmailfs.conf.

I tried the following command:
```

sudo mount -t gmailfs /usr/share/pycentral/gmailfs/site-packages/gmailfs.py /mnt

```

but I get the following error:

```

Ignored option :rw
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1130, in main
    server = Gmailfs(mountpoint, **namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 602, in __init__
    self.ga.login()
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 302, in login
    pageData = self._retrievePage(req)
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 331, in _retrievePage
    resp = urllib2.urlopen(req)
  File "/usr/lib/python2.5/urllib2.py", line 121, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 380, in open
    response = meth(req, response)
  File "/usr/lib/python2.5/urllib2.py", line 487, in http_response
    code, msg, hdrs = response.code, response.msg, response.info()
AttributeError: addinfourl instance has no attribute 'code'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport/python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1130, in main
    server = Gmailfs(mountpoint, **namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 602, in __init__
    self.ga.login()
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 302, in login
    pageData = self._retrievePage(req)
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 331, in _retrievePage
    resp = urllib2.urlopen(req)
  File "/usr/lib/python2.5/urllib2.py", line 121, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 380, in open
    response = meth(req, response)
  File "/usr/lib/python2.5/urllib2.py", line 487, in http_response
    code, msg, hdrs = response.code, response.msg, response.info()
AttributeError: addinfourl instance has no attribute 'code'

```

---

### Post by loskobosko on 2007-10-12
I get the same error, more or less.
i am behind a NAT, but actually i dnot' know if NAT does interfer with gmailfs. I can provide further details if needed.
[email]loskobosko@gmail.com[/email]

---

