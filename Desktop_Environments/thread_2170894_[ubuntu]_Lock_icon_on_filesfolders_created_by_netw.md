---
title: "[ubuntu] Lock icon on files/folders created by network users"
date: 2013-08-28
forum: Desktop Environments
---

### Post by vikram_kapoor on 2013-08-28
I have ubuntu, xubuntu, lubuntu, windows computers all on one network (LAN)

Now the computer having ubuntu has its **documents** folder shared on network in such a way that anyone can read/write/execute on it.
And whenever a **network user (xubuntu/windows/lubuntu)** creates a folder/file in the **shared documents** folder, that particular folder gets a lock icon like below and it no longer can be deleted from the ubuntu computer (as i don't own the file/folder). 

[IMG]http://img843.imageshack.us/img843/7586/50bf.png[/IMG]

Now, I do realize that I can easily **chmod** or **chown** it but I'll have to keep on doing it everytime someone adds a file/folder. Is there a permanent fix to this. Like disable this security feature or something ? Thanks.

---

### Post by zero2xiii on 2013-08-28
Hay,

Yes this is an easy fix:

```
gksudo gedit /etc/samba/smb.conf
```

find lines:
```
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700
```
AND
```
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 070
```

Change to:
```
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
**create mask = 0775**
```

```
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
**directory mask = 0775**
```

Note the semi colon is also missing (** ; **)

Save the file and reboot the system and the issue should be fixed :D

Cheers

EDIT:
I think you could actually just run these instead of reboot:
```
sudo restart smbd
sudo restart nmbd
```

---

### Post by vikram_kapoor on 2013-08-28
@[**[COLOR=#000000]zero2xiii[/COLOR]**]("http://ubuntuforums.org/member.php?u=1330915"), I thank you for such a detailed answer. It worked like a charm. You saved me a lot of work. Just the exact solution.

---

