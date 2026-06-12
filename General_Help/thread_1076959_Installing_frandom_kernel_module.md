---
title: "Installing frandom kernel module"
date: 2009-02-21
forum: General Help
---

### Post by Klaue on 2009-02-21
---
Ubuntu 8.10
Kernel version 2.6.27-11-generic
---

Hi there
I have some problems with installing the frandom kernel module from [http://www.billauer.co.il/frandom.html](http://www.billauer.co.il/frandom.html)

The reason I want to do this is because I have various disks which I want to overwrite with random data. I'd use DBAN, but the 2.0.0 beta (only one with USB support) throws an out-of-memory-error after 2-3 minutes. Now, I first tried /dev/urandom, but it's way too slow, only about 2 MB/sec (it's now running for about 10 hours and has not even finished the first half of the first disk) so I want to use frandom which is supposed to be 10 to 50 times faster

From the INSTALL file form frandom, shortened by me (after the make, which ran successfully and after a sudo -s):
(Note: full file and readme in attachment to this post)
> [COLOR="Red"]install -m 644 frandom.ko /lib/modules/`uname -r`/misc[/COLOR]
depmod -a
insmod frandom
mknod /dev/frandom c 235 11
chmod 444 /dev/frandom
mknod /dev/erandom c 235 12
chmod 444 /dev/erandom
[COLOR="Red"]adding "alias char-major-235 frandom" /etc/modules.conf[/COLOR]
adding "/sbin/modprobe frandom" to /etc/rc.local
the parts that I know are not working are red

First problem seems to be the install command. It just makes a new file called "misc" in the /lib/modules/`uname -r`/ dir (or at least I think it's new, I'm a bit afraid I'd ruin my system if I simply deleted it)
insmod frandom then tells me it doesn't find the file frandom
I also tried using
install -m 644 frandom.ko /lib/modules/`uname -r`/kernel/drivers/misc/frandom.ko
because I found some *.ko files in there, but insmod (or modprobe) still did not find frandom

The second problem (yet) is that there's no /etc/modules.conf in ubuntu. I suppose it should go in /etc/modprobe.d/aliases but I can't be sure until the first problem is solved

Can anyone help me? My expertise in installing modules ends at "modprobe <modulename" ;)

---

### Post by Klaue on 2009-02-22
bump

---

### Post by Klaue on 2009-02-22
*head->desk*

install -m 644 frandom.ko /lib/modules/`uname -r`/kernel/drivers/misc/
was correct, I probably just forgot to run depmod -a

/etc/modprobe.d/aliases was also correct

Comparison:

```
klaue@klaue-desktop:~$ dd if=/dev/urandom of=/dev/null
211903+0 Datensätze ein
211902+0 Datensätze aus
108493824 Bytes (108 MB) kopiert, 19.6147 s, 5.5 MB/s
```

```
klaue@klaue-desktop:~$ dd if=/dev/frandom of=/dev/null
2148375+0 Datensätze ein
2148374+0 Datensätze aus
1099967488 Bytes (1.1 GB) kopiert, 7.41137 s, 148 MB/s
```

```
klaue@klaue-desktop:~$ dd if=/dev/erandom of=/dev/null
2566001+0 Datensätze ein
2566001+0 Datensätze aus
1313792512 Bytes (1.3 GB) kopiert, 8.48057 s, 155 MB/s
```

---

### Post by chmac on 2009-08-24
Thanks for sharing your success here.

For anyone who missed it in Klaue's original message, use **/etc/modprobe.d/aliases instead of /etc/modules.conf**.

That was my only issue, now frandom works and is loaded automatically. :-)

---

