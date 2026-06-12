---
title: "Deleted ROOT account"
date: 2006-09-17
forum: Desktop Environments
---

### Post by ashrack on 2006-09-17
I was trying to hack into the root account in my VMWARE's UBUNTU install.

But apperantly instead of doing the following things in VMWARE's UBUNTU I did it on my real desktop UBUNTU DAPPER installation.
This is what I did:
I deleted the root line from /etc/shadow, /etc/passwd
and after did:
```
userdel -r root
```

So now am without root, SUDO gives me the following:
```
tom@tomi:~$ sudo
sudo: no passwd entry for root!

```
So what can I do?

---

### Post by lamego on 2006-09-17
1. If you are using vmware to do some disrupt first create a backup or a snapshot of the image while it is still working

2. boot from the Live CD, mount your root partition, and revert waht you did,

```
/etc/passwd:root:x:0:0:root:/root:/bin/bash
/etc/shadow:root:*:13405:0:99999:7:::

```

3. Avoid doing dumb things on the future

---

### Post by ashrack on 2006-09-19
tanx LAMENGO. It now partly works.
But I still don't have a root account since I deleted it with the following command:
```
userdel -r root
```

And thus I get this error:
```
tom@tomi:~$ sudo -s -H
id: cannot find name for group ID 0

```

EDIT:
created group ROOT at ID0. And set the accounts 'root' primary group to 'root' and gave it all the priviligies possible.
And now I believe it works normal.

So is this correct now:
```
tom@tomi:~$ id root
uid=0(root) gid=0(root) groups=0(root),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin)

```

---

### Post by stareye on 2007-09-28
What is the code you used to restore your root account? I did a similar thing in a different way, but am not extremely linux savy.

---

