---
title: "Trac troubleshooting help"
date: 2009-06-10
forum: General Help
---

### Post by jon.mithe on 2009-06-10
Hi,

I have a home setup with Apache, Trac and SVN.  I recently upgraded to 9.04 (from 8.10) and my Trac seems to of been canned in the process :/  I'm a bit stuck so wandering if anyone can help! :P 

The problem in a little more detail... I try and access my trac page through apache via the localhost and I get an Internal server error, random gumph and at the end:

```
Apache/2.2.11 (Ubuntu) DAV/2 SVN/1.5.4 PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_python/3.3.1 Python/2.6.2
```

From what I have been reading, this might of been caused by the upgrade installing python 2.6.x and I'm not 100% on this, but I believe trac is installed in?: (the folder and a bunch of python files are in there, is this the only directory it is installed in?)

```
/usr/lib/python2.5/site-packages/Trac-0.11b1-py2.5.egg/
```

and I have a python2.6 directory, but with no site-packages in.

So I'm thinking I need to install the latest version into the python 2.6 there and delete the older 2.5 version?

I'm being carful to not loose my trac environments / projects. I noticed a folder 

```
/var/trac
```

I'm guessing thats that folder containing all my projects (seems to have directories for projects, with a database file in it).  Probably would be worth backing that up... :P

So, I'm guessing I just need to delete that trac folder in the python2.5 dir and install the latest trac into python2.6 somehow?

I checked my /etc/apache2/sites-enabled$ and theres nothing point to the track, so I persume its just picking up the latest version of python.  Also points to the var/trac dir so guessing installing the new version and everything should work.

My svn works fine which is good :)

Any help/thoughts/confirmation of this would be a great help thanks

Cheers, 
Jon


edit: I'm seeing this in my /var/log/apache2/error.trac.log.

```
[Wed Jun 10 23:43:14 2009] [error] [client 127.0.0.1]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch\n    default=default_handler, arg=req, silent=hlist.silent)
[Wed Jun 10 23:43:14 2009] [error] [client 127.0.0.1]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1202, in _process_target\n    module = import_module(module_name, path=path)
[Wed Jun 10 23:43:14 2009] [error] [client 127.0.0.1]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 304, in import_module\n    return __import__(module_name, {}, {}, ['*'])
[Wed Jun 10 23:43:14 2009] [error] [client 127.0.0.1] ImportError: No module named trac.web.modpython_frontend
```

which sounds like thats not finding things in 2.6, unsuprisingly

---

### Post by jon.mithe on 2009-06-10
yeah downloading the new version and installing fixed it, i.e.

```

tar -xzvf <trac tar>
cd <trac extract dir>
sudo python ./setup.py install
```

Sounds like the trac files in the python is the only thing trac installs and just needs deleting.

---

