---
title: "Admin/Root Rights"
date: 2011-02-12
forum: Desktop Environments
---

### Post by Ihsan_Cingisiz on 2011-02-12
Hello,

I'm a new Ubuntu user and a Python programmer, it's the
first time that I use Python in Ubuntu so it's a bit c-
onfusing me. If I want to save a Module or something in
a specified map, I get 'Errno 13', it says that I don't 
have permission to edit, do thing in that map. And this
is also for importing files with Python. I logged in f-
rom Terminal with 'sudo -i' and closed Terminal, but the
problem keeps repeating. How do I login as Admin or Root
and stay as Admin or Root? I need right to edit/read fi-
les awell as root and normal user. An example:

Python file:
test.py -> 
test = open('/a.txt', 'w')
test.write('Test - Test - Test')
test.close

When I execute this, I get in the Python IDLE the 'Errno 13'
problem and below the 'Errno 13' it says that I don't have
permission.

Who know how to stay logged in as root, even if the user has
not logged in or isn't this possible, if it isn't then I just
want to get helped with the moving files, editing/reasing etc.

Thanks!

K. Regards,
I. C.

---

### Post by w3rt on 2011-02-12
you can enable a root terminal and use that to do the tasks that you need to perform

---

### Post by ankspo71 on 2011-02-12
Hi,
If I am  not mistaken, sudo times out in 5 or 10 minutes.
You can change this behavior though, see the link below:
[http://www.webupd8.org/2010/04/how-to-change-sudo-password-time-out-in.html](http://www.webupd8.org/2010/04/how-to-change-sudo-password-time-out-in.html)

This Foresite tutorial covering the same topic says to be extra careful modifying the above mentioned file...
[http://forum.foresightlinux.org/index.php?topic=504.0](http://forum.foresightlinux.org/index.php?topic=504.0)
Hope this helps.

---

### Post by debd on 2011-02-12
if you are using an IDE you can run it with root privilages to avoid problems.

> gksudo <name of application>

......like to open Geany in root mode

> gksudo geany

---

### Post by linuxsyst on 2011-02-12
try (ctrl+alt+f1)to f6 is command mode and (alt+f7) is to get back.
please answer.

---

### Post by CharlesA on 2011-02-12
The prefered way to access a root shell in Ubuntu is using this:

```
sudo -i
```

See here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ihsan_Cingisiz on 2011-02-12
> **CharlesA said:**
> The prefered way to access a root shell in Ubuntu is using this:

```
sudo -i
```

See here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Hmm... I did this but I still can't delete files with admin/root rights. I found a way to open apps as root but I just need to know
how to delete files that are protected with admin/root rights.

---

### Post by Ihsan_Cingisiz on 2011-02-12
> **Ihsan_Cingisiz said:**
> Hmm... I did this but I still can't delete files with admin/root rights. I found a way to open apps as root but I just need to know
how to delete files that are protected with admin/root rights.

Nevermind. I found a solution for all this :D!

I do alt+f2 -> gksudo nautilus -> Delete/Edit files from here ;)

---

### Post by Ihsan_Cingisiz on 2011-02-12
> **Ihsan_Cingisiz said:**
> Hmm... I did this but I still can't delete files with admin/root rights. I found a way to open apps as root but I just need to know
how to delete files that are protected with admin/root rights.

Nevermind. I found a solution for all this :D!

I do alt+f2 -> gksudo nautilus -> Delete/Edit files from here ;)

I thank ya'll for trying to help me!
I hope someone else will get helped with this too..

Regards

---

### Post by debd on 2011-02-13
now mark this thread as solved!

---

