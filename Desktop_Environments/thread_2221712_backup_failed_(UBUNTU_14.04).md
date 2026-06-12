---
title: "backup failed (UBUNTU 14.04)"
date: 2014-05-03
forum: Desktop Environments
---

### Post by tempspasse1 on 2014-05-03
backup failed Traceback (most recent call last):   File "/usr/bin/duplicity", line 1494, in      with_tempdir(main)   File "/usr/bin/duplicity", line 1488, in with_tempdir     fn()   File "/usr/bin/duplicity", line 1337, in main     do_backup(action)   File "/usr/bin/duplicity", line 1463, in do_backup     full_backup(col_stats)   File "/usr/bin/duplicity", line 542, in full_backup     globals.backend)   File "/usr/bin/duplicity", line 405, in write_multivol     at_end = gpg.GzipWriteFile(tarblock_iter, tdp.name, globals.volsize)   File "/usr/lib/python2.7/dist-packages/duplicity/gpg.py", line 383, in GzipWriteFile     new_block = block_iter.next()   File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 515, in next     result = self.process_continued()   File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 695, in process_continued     data, last_block = self.get_data_block(self.process_fp)   File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 681, in get_data_block     if fp.close():   File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 435, in close     self.callback(self.sig_gen.getsig(), *self.extra_args)   File "/usr/lib/python2.7/dist-packages/duplicity/librsync.py", line 214, in getsig     return ''.join(self.sigstring_list) MemoryError

---

### Post by udo4 on 2014-07-27
I'm getting a similar failure in Ubuntu 14.04 every time I try to run the built in backup utility. I just recently switched to Ubuntu from Windows, still learning. Is there anything that I'm doing wrong?

---

### Post by Ron_Callison on 2014-08-17
Same here

---

