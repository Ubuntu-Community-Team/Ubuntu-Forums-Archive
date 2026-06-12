---
title: "Re: Synaptic Package Manager ERROR - dpkg interrupted"
date: 2009-03-08
forum: General Help
---

### Post by kkzman on 2009-03-08
I am having the same problem E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct problem
E:_cache-> open()failed, Please report.

Iran the dpkg --configure -a and got this message

root@kevin-desktop:/home/kevin# dpkg --configure -a
Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error
dpkg: subprocess post-installation script returned error exit status 135
root@kevin-desktop:/home/kevin#


Can anyone please help?

---

### Post by dcstar on 2009-03-09
> **kkzman said:**
> I am having the same problem E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct problem
E:_cache-> open()failed, Please report.

Iran the dpkg --configure -a and got this message

root@kevin-desktop:/home/kevin# dpkg --configure -a
Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error
dpkg: subprocess post-installation script returned error exit status 135
root@kevin-desktop:/home/kevin#


Can anyone please help?

"Bus error" indicates a hardware problem, reboot and try again.

---

### Post by kkzman on 2009-03-09
I have rebooted and reran dpkg --configure -a and still   getting the same message.

How do  I figure  out what piece of hardware is not functioning properly

---

### Post by daylongest on 2009-03-10
I am having the same problem E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct problem
E:_cache-> open()failed, Please report.
This first happened yesterday, so have we all suffered the same hardware failure simultaneously ?
I can't open my Package Manager to attempt the above run command because the error message pops up with the Manager and when I remove the popup, the Manager goes too. Re-booting doesn't help. Sorry if I'm being thick here but I'm a newbie and would really appreciate help as it seems I can't install any updates till this is sorted.

---

### Post by Yellow Pasque on 2009-03-10
Are you running the command with root privileges? (You should)
```
sudo dpkg --configure -a
```

---

### Post by 3rdalbum on 2009-03-10
daylongest: You're not thick, you just need to do a search on the forums for that error message - I see a new post about this every couple of days with the correct solution.

When it tells you to run dpkg --configure -a, you must go to the terminal and type this command:

```
sudo dpkg --configure -a
```

The "sudo" is necessary because package management can only be done by the root user, and the "sudo" before the command says "Run this as root".

---

### Post by daylongest on 2009-03-10
Many thanks 3rdalbum. You are the 'bee's knees' It worked a treat (Once I found out how to open a terminal window !)

---

### Post by kkzman on 2009-03-17
Well  I  have rebooted and still having the same problem.

any other ideas as to what I can do?????????

---

### Post by Yellow Pasque on 2009-03-17
[http://ubuntuforums.org/showpost.php?p=4040893&postcount=10](http://ubuntuforums.org/showpost.php?p=4040893&postcount=10)

---

