---
title: "Ubuntu Install Error"
date: 2009-04-23
forum: General Help
---

### Post by Spiritous on 2009-04-23
Sorry if i posted in wrong place... 

I try to install the CD Boot Helper as I can't boot from the CD (Tried several times)and it gets stuck on;

Installing CD boot helper.

Error Code:
An error occurred:
Permission denied
For more information, please see the log file: C:\docume~1\account\temp\wubi-9.04-rev128.log


For the bit in the log with error:
IOError: [Errno 13] Permission denied
04-23 17:59 DEBUG  TaskList: # Cancelling tasklist
04-23 17:59 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 119, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 216, in run_cd_boot
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
04-23 17:59 DEBUG  TaskList: New task check_iso
04-23 17:59 DEBUG  TaskList: ## Finished use_cd
04-23 17:59 DEBUG  TaskList: # Finished tasklist


Hope you can help :(

---

