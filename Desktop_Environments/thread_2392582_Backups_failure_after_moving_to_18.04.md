---
title: "Backups failure after moving to 18.04"
date: 2018-05-22
forum: Desktop Environments
---

### Post by cvgaviao on 2018-05-22
hello,
I'm getting a failure when trying to do the first backup after upgraded to 18.04.

Could someone give me a direction ?

Bellow is the message that is presented:

[PHP]Traceback (innermost last):
  File "/usr/bin/duplicity", line 1555, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1541, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1393, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1511, in do_backup
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 572, in full_backup
    globals.backend)
  File "/usr/bin/duplicity", line 454, in write_multivol
    (tdp, dest_filename, vol_num)))
  File "/usr/lib/python2.7/dist-packages/duplicity/asyncscheduler.py", line 146, in schedule_task
    return self.__run_synchronously(fn, params)
  File "/usr/lib/python2.7/dist-packages/duplicity/asyncscheduler.py", line 172, in __run_synchronously
    ret = fn(*params)
  File "/usr/bin/duplicity", line 453, in <lambda>
    vol_num: put(tdp, dest_filename, vol_num),
  File "/usr/bin/duplicity", line 342, in put
    backend.put(tdp, dest_filename)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 395, in inner_retry
    % (n, e.__class__.__name__, util.uexc(e)))
  File "/usr/lib/python2.7/dist-packages/duplicity/util.py", line 79, in uexc
    return ufn(unicode(e).encode('utf-8'))
 UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 37: ordinal not in range(128)[/PHP]

---

