---
title: "COM port under Wine"
date: 2009-03-27
forum: General Help
---

### Post by swordfishRU on 2009-03-27
Hi, all!

I need serial port access under Wine. I did all things I had found in forums, but I have no access. 
What went wrong?

-------------------------------------------------------
hm@m-art:~$ cat /proc/version
Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009

hm@m-art:~$ wine --version
wine-1.1.17

hm@m-art:~$ who | grep tty7
hm       tty7         2009-03-28 17:15 (:0)

hm@m-art:~$ ls -all /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 2009-03-28 17:14 /dev/ttyS0

hm@m-art:~$ cat /etc/group | grep hm | grep dialout
dialout : x : 20 : hm

hm@m-art:~$ ls -all ./.wine/dosdevices/ | grep tty
lrwxrwxrwx 1 hm hm   10 2009-03-21 20:20 com1 -> /dev/ttyS0
-------------------------------------------------------

I don't see com1 device in Wine configuration tool, and windOFFs hyperterm don't show com1 device in list of 'connect using' combo box list.

Thanks!

---

### Post by swordfishRU on 2009-03-28
up

---

### Post by 3Miro on 2009-03-28
I have never done that. Have you looked around the winehq forums?

---

