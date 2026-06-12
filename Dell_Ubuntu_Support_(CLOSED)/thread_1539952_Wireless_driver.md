---
title: "Wireless driver"
date: 2010-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Htet Naing on 2010-07-27
I need wireless driver for Ubuntu 10.04 LTS.
My laptop is Dell Inspiron 1464
Is there anyone who can help me?

---

### Post by realzippy on 2010-07-27
If it is this
[http://www.handingchao.com/new-dell-inspiron-1464-14-inch-laptop-review/](http://www.handingchao.com/new-dell-inspiron-1464-14-inch-laptop-review/)

laptop and has a *Dell 1520 WLAN card*,have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1443776](http://ubuntuforums.org/showthread.php?t=1443776)

---

### Post by iponeverything on 2010-07-27
Go to:

System -> Administration -> Hardware Drivers 


To see if has a proprietary driver available.

---

### Post by realzippy on 2010-07-27
If nothing helps,please post the output of:

```
lspci
```

---

### Post by DukeBoxer on 2010-07-27
I'm having the same sort of problem, but I did all that, added "wl" to my /etc/modules file and I still can't get the wireless to detect any networks.

First I installed the broadcom driver and the computer saw all wireless networks, then my problem was I couldn't connect to my network because it wouldn't accept the password, so I updated, upgraded, dist-upgraded, restarted and now nothing. Maybe it has something to do with the new 2.6.32-24 kernel they just pushed out.

This is happening on a brand new Dell Inspiron N5010

---

### Post by Htet Naing on 2010-07-30
> **realzippy said:**
> If it is this
[http://www.handingchao.com/new-dell-inspiron-1464-14-inch-laptop-review/](http://www.handingchao.com/new-dell-inspiron-1464-14-inch-laptop-review/)

laptop and has a *Dell 1520 WLAN card*,have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1443776](http://ubuntuforums.org/showthread.php?t=1443776)
I can't find driver software for my laptop at the above links.:(

---

### Post by ptn107 on 2010-07-30
I had a similar problem with my studio 1749.  I installed the Broadcom STA drivers (I manually installed the packages: bcmwl-kernel-source patch dkms) then I was able to see a list of wireless networks.  I tried connecting but it would not connect to any.  Just to try I pressed my wireless key and then tried reconnecting.  It worked.  Long story short whether your wireless is enabled or disabled and you have the drivers installed, you will still see a listing of networks you will just not be able to connect.  So try pressing the wireless button on your keyboard and try again.

---

### Post by ugm6hr on 2010-07-31
As per preivous advice, confirm what your wifi card is by giving us the output from:
```
lspci
lshw -class network
```

---

### Post by Baba-Juju on 2010-08-22
> **DukeBoxer said:**
> I'm having the same sort of problem, but I did all that, added "wl" to my /etc/modules file and I still can't get the wireless to detect any networks.

First I installed the broadcom driver and the computer saw all wireless networks, then my problem was I couldn't connect to my network because it wouldn't accept the password, so I updated, upgraded, dist-upgraded, restarted and now nothing. Maybe it has something to do with the new 2.6.32-24 kernel they just pushed out.

This is happening on a brand new Dell Inspiron N5010
I just bought a Dell Inspiron N5010 and installed Ubuntu 10.4 kernel 2.6.32-24-generic. Everyhting so far works smoothly including wireless.

---

