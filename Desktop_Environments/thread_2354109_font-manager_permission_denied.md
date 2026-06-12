---
title: "font-manager permission denied"
date: 2017-02-28
forum: Desktop Environments
---

### Post by jason-b-freeman on 2017-02-28
I installed the Microsoft Core fonts on my system.  In the process of doing this I also installed font-manager (which I like).  Long story short, font-manager doesn't install fonts system wide when you run the tool using elevated privileges.  It installed it in my ~/.fonts folder with a link to the ~/.local/share/font-manager/Library.  I moved the installed fonts to /user/share/fonts/msttcorefonts and deleted my ~/.fonts and ~/.local/share/font-manager directories.  When I now run font-manager without elevated privileges it briefly opens and then closes.  Runnning from the CLI gives the following:

```
jason@galactica:~
$ font-manager
INFO    :  Verified /home/jason/.fonts.conf
INFO    :  Font Manager is now starting
Traceback (most recent call last):
  File "/usr/bin/font-manager", line 98, in <module>
    main()
  File "/usr/bin/font-manager", line 89, in main
    Main()
  File "/usr/share/font-manager/main.py", line 98, in __init__
    self.objects.load_core()
  File "/usr/share/font-manager/main.py", line 425, in load_core
    self.data['FontManager'] = core.get_manager(self.data['MainWindow'])
  File "/usr/share/font-manager/core/__init__.py", line 791, in get_manager
    MANAGER = FontManager(PROGRESS_CALLBACK, parent)
  File "/usr/share/font-manager/core/__init__.py", line 177, in __init__
    core.fonts.Sort(self, self.progress, self.parent)
  File "/usr/share/font-manager/core/fonts.py", line 290, in __init__
    self._check_cache()
  File "/usr/share/font-manager/core/fonts.py", line 344, in _check_cache
    protocol=cPickle.HIGHEST_PROTOCOL)
  File "/usr/lib/python2.7/shelve.py", line 243, in open
    return DbfilenameShelf(filename, flag, protocol, writeback)
  File "/usr/lib/python2.7/shelve.py", line 227, in __init__
    Shelf.__init__(self, anydbm.open(filename, flag), protocol, writeback)
  File "/usr/lib/python2.7/anydbm.py", line 85, in open
    return mod.open(file, flag, mode)
  File "/usr/lib/python2.7/dbhash.py", line 18, in open
    return bsddb.hashopen(file, flag, mode)
  File "/usr/lib/python2.7/bsddb/__init__.py", line 364, in hashopen
    d.open(file, db.DB_HASH, flags, mode)
bsddb.db.DBAccessError: (13, 'Permission denied')
```

Googling sadly did not return relevant results :(

Ideas?

-Jason

---

### Post by &amp;KyT$0P# on 2017-02-28
Please post the output from running this command in Terminal -
```
find ~ -user root
```

---

