---
title: "vmware reconfig"
date: 2006-09-20
forum: Desktop Environments
---

### Post by comppsyco on 2006-09-20
I have been happily running vmware server for awhile now to use Yahoo Music. After the last kernel update it stopped working and asked me to run the command
```
/usr/bin/vmware-config.pl
```I did, and I use the defaults for all the options until I get to this:
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

```

Huh? Help please! I need my music!

---

### Post by NetworkGuy on 2006-09-20
You need to install the linux-headers for the kernel you are running.

---

### Post by comppsyco on 2006-09-20
And I do that how?

---

### Post by NetworkGuy on 2006-09-20
From synaptic, find the linux-headers and then install the file that matches the kernel you are running.

```
uname -r
```
shows the version of the kernel you are running.

---

### Post by tagra123 on 2006-09-20
```
sudo apt-get install linux-headers-`uname -r`
```

The marks before and after `uname -r` are backtics (same key tilde key)

---

### Post by comppsyco on 2006-09-20
Thanks! everything's working perfectly now.

---

