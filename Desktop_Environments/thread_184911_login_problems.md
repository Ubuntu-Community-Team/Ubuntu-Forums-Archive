---
title: "login problems"
date: 2006-05-30
forum: Desktop Environments
---

### Post by rem on 2006-05-30
Hi everybody,

Have a stupid problem when booting and logging in ... I tried to enable the samba server and messed up with some commands i found in the dapper guide ...When rebooted the system, my login password is no longer working. Can't login anymore !!! Please, can you help me please? I hope another install is out of discussion here since I just cleaned install the system from Breezy and set up my system and programs.

Any help would be so appreciated!

Thanks a lot in advance...

---

### Post by Ramses de Norre on 2006-05-30
Boot recovery mode and do ```
passwd user_name new_password
``` to set a new password.

---

### Post by konradsa on 2006-05-30
[QUOTE=rem]Hi everybody,

Have a stupid problem when booting and logging in ... I tried to enable the samba server and messed up with some commands i found in the dapper guide ...When rebooted the system, my login password is no longer working. Can't login anymore !!! Please, can you help me please? I hope another install is out of discussion here since I just cleaned install the system from Breezy and set up my system and programs.

Any help would be so appreciated!

Thanks a lot in advance...[/QUOTE]


I once had this problem when I had a login script that tried to write to a file that did not exist and gave me an error. The effect was that although my user/pass was correct, I just heard the drums and ended up on the login screen again. See if you have set up some script to run after login that does not work. You may need to boot in recovery mode to figure that out.

Sascha

---

### Post by rem on 2006-05-30
thanks a million guys, i really appreciate it... such a fast reply...
got everything, but how can i boot in recovery mode???

---

### Post by kingmonkey on 2006-05-30
Restart your computer and at the grub menu select recovery

---

### Post by rem on 2006-05-30
i finally managed to find out which the password was...
actually i think i changed it myself, but (please don't laugh) i must had the caps lock on... anyway, good to be back.

thanks a lot guys for your help, don't know how i would manage without your help... even the password problem is solved, i would like to know about the recovery mode thing. maybe another time when needed, i will not waste your time anymore.

i rebooted my pc but don't have any "recovery mode" option. it just simply fires up ubuntu dapper... counting from 5 to 0 then start!

---

