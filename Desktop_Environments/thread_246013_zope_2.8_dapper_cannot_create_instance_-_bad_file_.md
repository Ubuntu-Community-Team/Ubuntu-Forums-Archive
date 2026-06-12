---
title: "zope 2.8 dapper cannot create instance - bad file permissions"
date: 2006-08-28
forum: Desktop Environments
---

### Post by jamespi on 2006-08-28
i have apt-getted zope, then i put in the following things to try and make an instance in my home folder (for later use with plone):

> python /usr/lib/zope2.8/bin/mkzopeinstance.py
Please choose a directory in which you'd like to install
Zope "instance home" files such as database files, configuration
files, etc.

Directory: ~/zope/instances/plone
Please choose a username and password for the initial user.
These will be the credentials you use to initially manage
your new Zope instance.

Username: ploneuser
Password:
Verify password:
Traceback (most recent call last):
  File "/usr/lib/zope2.8/bin/mkzopeinstance.py", line 222, in ?
    main()
  File "/usr/lib/zope2.8/bin/mkzopeinstance.py", line 163, in main
    copyzopeskel.copyskel(skelsrc, skeltarget, uid, gid, layout, **kw)
  File "/usr/lib/zope2.8/bin/copyzopeskel.py", line 206, in copyskel
    uid, gid)
  File "/usr/lib/zope2.8/bin/copyzopeskel.py", line 285, in movedir
    os.rename(target, backup)
OSError: [Errno 13] Permission denied


if i run mkzopeinstance as sudo, it creates an instance. the instance can then only be started with sudo

is this a bug? cos the plone website specifically tells you not to use sudo to run mkzopeinstance.

i know this is a roundabout way of doing things, but when i apt-get installed "plone-site" i couldn't find where the plone product was kept. so i wiped it all off with synaptic but then deleted stuff from etc and var that got left behind and now apt-get plone-site exits with error 13 "couldn't preconfigure" or something like that. i tried to install zope from the latest tarball but make wouldn't work, it gave a torrent of errors that run off the top of my terminal buffer. and i know NOTHING about C or compiling it.

---

