---
title: "Skype cannot login"
date: 2006-04-06
forum: Desktop Environments
---

### Post by anodizer on 2006-04-06
..well actually it can, but only when running it as root. I don't know why it happened cause some days before it was running perfectly without using sudo.
Any ideas? Or just a way to make a shortcut which will ask for root password cause it's disturbing opening a terminal and typing sudo /usr/local/bin/skype_dsp_hijacker every time.

---

### Post by waster on 2006-04-07
Don't know about dsp hijaker. Probably /dev/dsp problem, though. Is your user in the 'audio' group? /dev/dsp should be read/writable by everyone, if not, by root user and audio group with perms 660. Skype fails to log in if it can't get /dev/dsp.

---

### Post by anodizer on 2006-04-07
Yes my user is in the 'audio' group, the Use Audio Devices option is enabled in 'Users and Groups' menu. I changed permissions of /dev/dsp to 777 but it didn't help.

---

### Post by waster on 2006-04-07
you could try
strace skype 2>&1 | grep denied
or something like that. n.b. There are usually lots of file not found errors as binaries search the path for libraries.

---

### Post by anodizer on 2006-04-07
[QUOTE=waster]you could try
strace skype 2>&1 | grep denied
or something like that. n.b. There are usually lots of file not found errors as binaries search the path for libraries.[/QUOTE]

Here' the output:
```
$ strace skype 2>&1 | grep denied
open("/etc/qt3/.qtrc.lock", O_RDWR|O_CREAT|O_LARGEFILE, 0600) = -1 EACCES (Permission denied)
open("/etc/qt3/.qt_plugins_3.3rc.lock", O_RDWR|O_CREAT|O_LARGEFILE, 0600) = -1 EACCES (Permission denied)
open("/etc/qt3/.kstylerc.lock", O_RDWR|O_CREAT|O_LARGEFILE, 0600) = -1 EACCES (Permission denied)
open("/etc/qt3/.qtrc.lock", O_RDWR|O_CREAT|O_LARGEFILE, 0600) = -1 EACCES (Permission denied)
open("/etc/qt3/.lipstikstylerc.lock", O_RDWR|O_CREAT|O_LARGEFILE, 0600) = -1 EACCES (Permission denied)

```

I don't believe that qt is connected somehow with the online status, what do you think?
Btw, is there any way I can run skype in verbose mode?

---

### Post by waster on 2006-04-10
It almost certainly is connected. Skype can't login if it can't get DSP. It may fail strangely for other things.

These perms might be because you ran something as root. Use sudo chown you on those files (and check they have rw perm for owner), and try again.

---

