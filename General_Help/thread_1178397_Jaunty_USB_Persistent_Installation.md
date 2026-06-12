---
title: "Jaunty USB Persistent Installation"
date: 2009-06-04
forum: General Help
---

### Post by drbold on 2009-06-04
I have been able to get Jaunty to boot on up on a pendrive.
It is a 16gb Kingston. People have mentioned that persistent installation can cause memory wear on the usb pen drive.
I don't have a hard drive on this machine, and I don't want to install a new hard drive onto this laptop. 
I think I have disabled the swap file in my /etc/fstab file.
doing cat /proc/swaps shows this
filename                type           size  used  priority
/dev/ramzswap0          partition     123156 0     100

Does the above imply the flash drive is not being used for swapping?

Also I have heard the tmp directories will also cause memory wear.
I added this line to my /etc/fstab 
none /tmp        tmpfs     size=56M,mode1777     0 0 
How do I know that this was successful?
Also how can I monitor the read and writes to my usb pen drive?

Thank you in advance.

---

### Post by Mighty_Joe on 2009-06-10
You can turn off swapping by entering the line:
```
vm.swappiness=0
```
in your /etc/sysctl.conf file ([see here]("http://www.linuxhowtos.org/Tips%20and%20Tricks/ulimit.htm"))

As for tmp directories, I set mine up like so:
```

    tmpfs      /tmp                    tmpfs        defaults      0 0
    tmpfs      /var/tmp                tmpfs        defaults      0 0
    tmpfs      /var/lock               tmpfs        defaults      0 0
    tmpfs      /var/log                tmpfs        defaults      0 0

```
[see this document]("http://beastie.cs.ua.edu/cs150/configuration.html") for that and other tweaks.

---

