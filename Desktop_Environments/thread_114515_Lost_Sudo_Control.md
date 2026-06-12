---
title: "Lost Sudo Control"
date: 2006-01-08
forum: Desktop Environments
---

### Post by xgreddy on 2006-01-08
Hi,
   I'm a new linux user and i have no idea how to fix this problem. I tried searching the forum for any similar post but couldn't find any. I'm also not sure if i'm posting in the right thread so please be easy on me. I lost sudo control to my primary account after removing & readding my account to the "users and groups" so now whenever i try to do any administrative task like update, nothing would run after asking for my password. Any help is greatly appreciated. Thanks

---

### Post by stuporglue on 2006-01-08
Short version:
Log in as root using rescue mode, change the groups that your user is in.

Long version:
in Grub (the boot loader) choose your kernel version "rescue mode". It will boot you to a text only root prompt

su to your user then find what groups you're in
# su - YOUR_USER_NAME
$ groups
  adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin (this list may be different for you, in fact it will be, because you're not in the admin group any more!)

Go back to root
$ exit

Change groups you're a member of```

# usermod -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,scanner,admin YOUR_USER_NAME
```

Reboot and enjoy
# reboot



Hope that works. I haven't used usermod is a while, but I did double check the man page, so I think it's right.

---

