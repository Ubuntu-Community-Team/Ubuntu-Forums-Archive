---
title: "wubi don't ask to reboot"
date: 2009-05-19
forum: General Help
---

### Post by _kool on 2009-05-19
i am having a problem installing ubuntu using wubi.
when wubi finish download the ubuntu iso, he starts instaling(i think he is doing a copy of the ubuntu image). After that, say "extracting kernel". A few secunds later he just close.
Don't ask to reboot (like some printscreens i saw) and dont write to boot.ini(i manually can write in boot.ini).

Can someone help me?

my pc is a toshiba 1.6ghz 496mb ram windows XP home SP3.

My XP language is portuguese.


final lines of wubi-9.04-rev129.log:

05-19 13:06 DEBUG  TaskList: ## Finished extract_kernel
05-19 13:06 DEBUG  TaskList: ## Running choose_disk_sizes...
05-19 13:06 DEBUG  WindowsBackend: total size=7000
  root=6744
  swap=256
  home=0
  usr=0
05-19 13:06 DEBUG  TaskList: ## Finished choose_disk_sizes
05-19 13:06 DEBUG  TaskList: ## Running create_preseed...
05-19 13:06 ERROR  TaskList: 'ascii' codec can't decode byte 0xe1 in position 1: ordinal not in range(128)
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 578, in create_preseed
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe1 in position 1: ordinal not in range(128)
05-19 13:06 DEBUG  TaskList: # Cancelling tasklist
05-19 13:06 ERROR  root: 'ascii' codec can't decode byte 0xe1 in position 1: ordinal not in range(128)
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe1 in position 1: ordinal not in range(128)
05-19 13:06 DEBUG  TaskList: # Finished tasklist


ty

---

### Post by Bindsa on 2009-05-19
The problem seems to be the ASCII codec, not sure what precisely though.

---

### Post by _kool on 2009-05-19
> **_kool said:**
> i am having a problem installing ubuntu using wubi.
when wubi finish download the ubuntu iso, he starts instaling(i think he is doing a copy of the ubuntu image). After that, say "extracting kernel". A few secunds later he just close.
Don't ask to reboot (like some printscreens i saw) and dont write to boot.ini(i manually can write in boot.ini).

Can someone help me?

my pc is a toshiba 1.6ghz 496mb ram windows XP home SP3.

My XP language is portuguese.


final lines of wubi-9.04-rev129.log:

05-19 13:06 DEBUG  TaskList: ## Finished extract_kernel
05-19 13:06 DEBUG  TaskList: ## Running choose_disk_sizes...
05-19 13:06 DEBUG  WindowsBackend: total size=7000
  root=6744
  swap=256
  home=0
  usr=0
05-19 13:06 DEBUG  TaskList: ## Finished choose_disk_sizes
05-19 13:06 DEBUG  TaskList: ## Running create_preseed...
05-19 13:06 ERROR  TaskList: 'ascii' codec can't decode byte 0xe1 in position 1: ordinal not in range(128)
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 578, in create_preseed
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe1 in position 1: ordinal not in range(128)
05-19 13:06 DEBUG  TaskList: # Cancelling tasklist
05-19 13:06 ERROR  root: 'ascii' codec can't decode byte 0xe1 in position 1: ordinal not in range(128)
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe1 in position 1: ordinal not in range(128)
05-19 13:06 DEBUG  TaskList: # Finished tasklist


ty
Finally made it.
The problem was my windows user name.
I had an account name like "andré santos".
wubi used my account user name, and gave that encoding error because special chars like "é".
I created another account name without special and worked fine.
Seems like a "little bug" that take me some hours to find out...

Does any one know how to report this bug?

---

### Post by hggdh on 2009-05-19
> **_kool said:**
> Finally made it.
The problem was my windows user name.
I had an account name like "andré santos".
wubi used my account user name, and gave that encoding error because special chars like "é".
I created another account name without special and worked fine.
Seems like a "little bug" that take me some hours to find out...

Does any one know how to report this bug?

Yes. Please read [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) for starters; you can file a bug at [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug).

Thank you

---

### Post by Bindsa on 2009-05-19
> **_kool said:**
> Finally made it.
The problem was my windows user name.
I had an account name like "andré santos".
wubi used my account user name, and gave that encoding error because special chars like "é".
I created another account name without special and worked fine.
Seems like a "little bug" that take me some hours to find out...
 
Does any one know how to report this bug?
 
Ah know I understand where that ASCII error comes from, your username didn't exist of standard ASCII characters, that indeed is a bug. Thanks for finding out!

---

