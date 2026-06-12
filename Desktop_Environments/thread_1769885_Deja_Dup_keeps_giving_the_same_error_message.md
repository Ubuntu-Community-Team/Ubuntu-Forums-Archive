---
title: "Deja Dup keeps giving the same error message"
date: 2011-05-28
forum: Desktop Environments
---

### Post by Zylstra555 on 2011-05-28
Deja Dup keeps giving me the same error message when I try to back up my computer. It starts scanning for the first backup, and then prompts me with this error. 
The remote SFTP location I am backing up to is empty at this time. The issue also happens when I try to back up to an FTP location. 

I have the error at the end of my post for ease of reading. 

I went into my key manager and deleted the stored passwords for the backup location, and the password I wanted to use for encryption in Deja Dup. 

I uninstalled/reinstalled multiple times (with restarts in-between..) 

I ran   rm -r ~/.cache/deja-dup   after getting the error to try again -- still no success. 


Your assistance in the matter is more than apperciated. 
- J. Zylstra


```


Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1262, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1255, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1228, in main
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 408, in full_backup
    bytes_written = dummy_backup(tarblock_iter)
  File "/usr/bin/duplicity", line 161, in dummy_backup
    while tarblock_iter.next():
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 505, in next
    result = self.process(self.input_iter.next(), size)
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 187, in get_delta_iter
    for new_path, sig_path in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 279, in collate2iters
    for relem1 in riter1:
  File "/usr/lib/python2.7/dist-packages/duplicity/selection.py", line 174, in Iterate
    subpath, val = diryield_stack[-1].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/selection.py", line 143, in diryield
    error_handler, Path.append, (path, filename))
  File "/usr/lib/python2.7/dist-packages/duplicity/robust.py", line 37, in check_common_error
    return function(*args)
  File "/usr/lib/python2.7/dist-packages/duplicity/path.py", line 507, in append
    return self.__class__(self.base, self.index + (ext,))
  File "/usr/lib/python2.7/dist-packages/duplicity/path.py", line 487, in __init__
    self.setdata()
  File "/usr/lib/python2.7/dist-packages/duplicity/path.py", line 492, in setdata
    self.stat = os.lstat(self.name)
OSError: [Errno 107] Transport endpoint is not connected: '/home/jesse/.gvfs'
```

---

### Post by Zylstra555 on 2011-06-04
Anything? (6 days..)

---

### Post by vkapas on 2011-08-18
Try upgrading duplicity to the >= 6.13 version.
PPA: [https://launchpad.net/~duplicity-team/+archive/ppa](https://launchpad.net/~duplicity-team/+archive/ppa)

[More about this problem on launchpad]("https://bugs.launchpad.net/deja-dup/+bug/794576").

---

