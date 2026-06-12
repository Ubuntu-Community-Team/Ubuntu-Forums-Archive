---
title: "mldonkey-server dont start!"
date: 2005-05-09
forum: Desktop Environments
---

### Post by msxuser on 2005-05-09
hi!

mldonkey-server 2.5.28-2 works correctly on kubuntu? when i load with root "/etc/init.d/mldonkey-server start" does not function. but, when i load manually with the user mldonkey "/var/lib/mldonkey/mlnet" if functions!

the debug of error is with (/etc/init.d/mldonkey-server start):

May 7 16:50:57 master mlnet_error: Fatal error: exception Unix.Unix_error(8, "mkdir", "./incoming")

whats happening?

a lot of thanks

---

### Post by Knome_fan on 2005-05-09
I'm just guessing here, as I don't use mldonkey, but could it be that you don't have the right permissions to create ./incoming?

---

### Post by msxuser on 2005-05-09
[QUOTE=Knome_fan]I'm just guessing here, as I don't use mldonkey, but could it be that you don't have the right permissions to create ./incoming?[/QUOTE]

*...so I think that is a problem of script, because I can execute it without problems since the user mldonkey... some idea?*   ](*,) 


/var/lib/mldonkey/

rwxrwxrwx  1 mldonkey mldonkey       32 2005-04-25 17:38 incoming -> /home/media/shares/incoming/
lrwxrwxrwx  1 mldonkey mldonkey       28 2005-04-25 17:39 temp -> /home/media/shares/temp/

/home/media/shares/

drwxrwx---  2 mldonkey mldonkey   23 2005-05-07 21:16 incoming
drwxrwx---  2 mldonkey mldonkey 4096 2005-05-07 21:04 temp


thanks!

---

