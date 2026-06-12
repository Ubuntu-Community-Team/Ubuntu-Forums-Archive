---
title: "gDesklets is driving me nuts!!"
date: 2005-12-17
forum: Desktop Environments
---

### Post by chem199 on 2005-12-17
I am in Ubuntu Breezy, I have python 2.4 running, i installed gDesklets from synaptic, i downloaded the data files.  when i open shell and type gDesklet i get this error:

> altair@chemlab:~$ gdesklets

==========================================================[12/17/05-19:28:17]====== Unhandled error! Something bad and unexpected happened.

[EXC][Errno 13] Permission denied: '/home/altair/.gdesklets/Displays'
in /usr/bin/gdesklets: line 395 ?
in /usr/bin/gdesklets: line 32 check_user
in /usr/lib/gdesklets/utils/__init__.py: line 118 makedirs
in /usr/lib/python2.4/os.py: line 159 makedirs
[EXC]/usr/lib/python2.4/os.py

[---]  154         head, tail = path.split(head)
[---]  155     if head and tail and not path.exists(head):
[---]  156         makedirs(head, mode)
[---]  157         if tail == curdir:           # xxx/newdir/. exists if xxx/newdir exists
[---]  158             return
[ERR]> 159     mkdir(name, mode)
[---]  160
[---]  161 def removedirs(name):
[---]  162     """removedirs(path)
[---]  163
[---]  164     Super-rmdir; remove a leaf directory and empty all intermediate
[---]  165     ones.  Works like rmdir except that, if the leaf directory is


I have heard of many people having Unhandled Error, but the only solutions i have heard is uninstall and reinstall.  I have does that to no avail.  It has never worked, so there is no prefs for me to delete or edit.  If anyone has an idea how to fix this please help.  BTW it maybe a python programing error, i can't program so if you could talk to me as if i were three if it is that kind of problem, i would be very appreciative. I am not a compleate newbie but i do need some assistance.

Thanks
-- Aren

---

### Post by chem199 on 2005-12-17
nevermind, i'm a fool, i fixed it. i forgot to change the permission for the folder.

-- Foolish Aren

---

