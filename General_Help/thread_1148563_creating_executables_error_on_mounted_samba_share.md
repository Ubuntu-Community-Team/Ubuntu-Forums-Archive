---
title: "creating executables error on mounted samba share"
date: 2009-05-04
forum: General Help
---

### Post by sc0 on 2009-05-04
Computer Environment

1. File Server (Ubuntu 9.04 server) with samba shared drive
2. Desktop (Ubuntu 9.04 server + ubuntu-desktop + build-essential installed)[INDENT]Samba share mounted to /sambashare/
logged in as only user (admin group)
[/INDENT]So my problem is the following:

I have clean code Q.cpp which will compile if I'm in my home directory on my desktop
> cd ~
> g++ Q.cpp

=====================

But if I'm inside my /sambashare/src/ directory after copying Q.cpp there I get the following errors:
> cd /sambashare/src/
> g++ Q.cpp
/usr/bin/ld: reopening a.out: Permission denied

/usr/bin/ld: final link failed: Permission denied
collect2: ld returned 1 exit status

Now the problem I believe is that I cannot create executable files in /sambashare/src/ because chmod +x <filename> throws errors

>chmod +x test.out
>chmod: changing permissions of `test.out': Operation not permitted

What confuses me is if I do the above with sudo locally everything works, but logged in as my regular accout I am having permissing issues on /sambashare/src/ and the directory has the following premissions
> cd /sambashare
> ls -ltr
total 0
drwxrwxrwx 3 <...> <...>      0 2009-05-04 12:43 src

Anyone have an idea what is going on? I'm relatively new to setting up / administering linux.

Thanks

---

### Post by sc0 on 2009-05-04
nevermind, problem was not with samba but with my options given in my /etc/fstab regarding how it was mounted. just changed the umask :)

---

