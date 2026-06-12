---
title: "wubi install error - exception, cannot copy"
date: 2009-05-11
forum: General Help
---

### Post by Ed None on 2009-05-11
I CANNOT INSTALL BECAUSE OF THIS MESSAGE, ANY IDEAS?
THANKS, ED
 
 
 
 
 
05-11 11:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-11 11:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-11 11:32 DEBUG  CommonBackend: Searching for local ISO
05-11 11:32 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-11 11:32 DEBUG  TaskList: New task get_metalink
05-11 11:32 DEBUG  TaskList: ### Running get_metalink...
05-11 11:32 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > C:\ubuntu\install
05-11 11:32 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-11 11:32 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) > C:\ubuntu\install
05-11 11:32 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-11 11:32 DEBUG  TaskList: ### Finished get_metalink
05-11 11:32 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-11 11:32 DEBUG  TaskList: # Cancelling tasklist
05-11 11:32 DEBUG  TaskList: # Finished tasklist
05-11 11:32 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Cannot download the metalink and therefore the ISO

---

