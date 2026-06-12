---
title: "????????????&quot;mv: cannot stat `/var/lib/dpkg/status-old': No such file or directory&quot;??"
date: 2009-04-17
forum: General Help
---

### Post by wolfman1221 on 2009-04-17
I received this message while trying to upgrade. If anyone could help me with it, I would certainly appreciate it.

---

### Post by danwood76 on 2009-04-17
Can you upgrade from the terminal?

Open a gnome terminal (Applications -> Accessories -> Terminal)
And run the following commands:
```

sudo apt-get update
sudo apt-get upgrade

```

If you get the same error with the command line update then you could try createing this file manually, its basically an old copy of the dpkg status so will be find just copying the current one to it:
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old

```

---

### Post by wolfman1221 on 2009-04-17
This is what came back.


"cp: cannot stat `/var/lib/dpkg/status': No such file or directory"

---

### Post by danwood76 on 2009-04-17
Can you post the output of:
```

ls -ld /var/lib/dpkg

```
It sounds as if dpkg libs are missing (this is a really bad thing)

---

### Post by wolfman1221 on 2009-04-17
"drwxr-xr-x 8 root root 4096 2009-04-15 17:58 /var/lib/dpkg"

---

### Post by danwood76 on 2009-04-17
Oops, I meant to get a directory listing, at least the libs are there though.
Can you post the output of this instead:
```

ls -l /var/lib/dpkg

```

---

### Post by wolfman1221 on 2009-04-17
"total 5704
drwxr-xr-x 2 root root    4096 2009-04-10 03:29 alternatives
-rw-r--r-- 1 root root 1337790 2009-04-10 03:49 available
-rw-r--r-- 1 root root 1337790 2009-04-10 03:29 available-old
-rw-r--r-- 1 root root       8 2008-10-29 17:04 cmethopt
-rw-r--r-- 1 root root     758 2009-03-02 19:37 diversions
-rw-r--r-- 1 root root     659 2009-03-02 19:37 diversions-old
drwxr-xr-x 2 root root  258048 2009-04-10 03:49 info
-rw-r----- 1 root root       0 2009-04-15 19:33 lock
drwxr-xr-x 2 root root    4096 2008-09-03 08:03 parts
-rw-r--r-- 1 root root      65 2008-10-29 17:20 statoverride
-rw-r--r-- 1 root root      30 2008-10-29 17:19 statoverride-old
-rw-r--r-- 1 root root 1419071 2009-04-10 03:49 status.broke
-rw-r--r-- 1 root root 1419022 2009-04-10 03:29 status-broken
drwxr-xr-x 2 root root    4096 2008-10-17 03:01 tmp.ci
drwxr-xr-x 2 root root    4096 2009-04-10 03:49 triggers
drwxr-xr-x 2 root root    4096 2009-04-10 03:49 updates"

---

### Post by danwood76 on 2009-04-17
It looks like you might have some broken packages.
Did the command line upgrade give you any other errors?

try running these:
```

sudo dpkg --configure -a
sudo apt-get -f install

```
That should fix any dpkg errors caused by an interrupted install

---

### Post by wolfman1221 on 2009-04-17
That is what came back. 


"sudo dpkg --configure -a"


"dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory"


"sudo apt-get -f install"

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

---

### Post by danwood76 on 2009-04-17
Hehe sounds almost like a chicken and egg situation.

The status.broke file and the broken file look about the right size to be the actual status file.
You could try copying that to status then running the above two commands.

So:
```

sudo cp /var/lib/dpkg/status.broke /var/lib/dpkg/status

```

---

### Post by wolfman1221 on 2009-04-17
This is what came back.
"

wolfman1221@ubuntu:~$ sudo cp /var/lib/dpkg/status.broke /var/lib/dpkg/status
wolfman1221@ubuntu:~$ 

"

---

### Post by danwood76 on 2009-04-17
Yeah thats fine.

Then run:
```

sudo dpkg --configure -a
sudo apt-get -f install

```

And if they run without error try updating.
I think something broke during a package install (maybe a system crash/reboot?)

---

### Post by wolfman1221 on 2009-04-17
This is what came back.


"You have 7 broken packages on your system!

Use the "Broken" filter to locate them"

---

### Post by danwood76 on 2009-04-17
To fix broken packages open up synaptic (System -> Administration -> Synaptic)
Click edit and choose "fix broken packages" then click apply.
That should (hopefully) fix your problems.

Then run the update manager and cross your fingers!

---

