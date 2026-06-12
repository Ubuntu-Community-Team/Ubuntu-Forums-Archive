---
title: "networking driving me mad..any help appreciated.."
date: 2009-03-31
forum: General Help
---

### Post by ozguitarplayer on 2009-03-31
Hi,
I have 2 computers with Hardy Heron.
No.1 and No.2 computers.

Using Samba I have set up file sharing, with the same settings on both..

On both 1 & 2 I can see the shared folders on the other.
Comp 1 can open files on Comp 2 (have to supply password)
Comp 2 can see files but will not open the files on comp 1 (supply password but password is asked for again and again)

This is an on going problem that exists even after new installations of o/s and it's so frustrating as I have to manually transfer files from 2 to 1

any help would be greatly appreciated

---

### Post by cariboo on 2009-03-31
Have you setup a samba password, if not open a terminal and type:

```
sudo smbpasswd -L -a <username>
```

then enable the user:

```
sudo smbpasswd -L -e <username>
```

where <username> is your username without the brackets.

Jim

---

### Post by ozguitarplayer on 2009-03-31
wow...so easy yet miles away if you don't know how...I read everything I could and can't remember anything about passwords or any prompts when setting up samba.
Thanks heaps Jim

if you're still there...how would I use terminal to change the password if I wanted to, would I just re-run the commands?

Nigel

---

