---
title: "Second user can't halt computer"
date: 2006-09-22
forum: Desktop Environments
---

### Post by thhp on 2006-09-22
Hi,

Apologies if this is a FAQ -- I've searched the forums and checked out the user manual but to no avail!

My problem is as follows:

I have two users for my Ubuntu systems: myself and my partner. My user was added first to the system on installation; and my partner's user was added later. My user has an option for turning off the computer; my partner's doesn't.

My initial assumption was that I belong to some group she doesn't, so I had a look:

```

thhp@orangutang:~$ cat /etc/group | grep thhp | grep -v flo
thhp:x:1000:
fuse:x:117:thhp

```

...but I couldn't see anything amiss.

Anyone got any suggestions?


Thanks,


Tom

---

### Post by ayoli on 2006-09-22
add your second user to admin group:
```
sudo adduser *your_second_username* admin
```

---

### Post by NetworkGuy on 2006-09-22
In Linux, you must be someone with root access to be able to shutdown a computer.  It's much different than Windows where anyone who can sign into the computer can shut it down and sometimes shut it down without signing in.

---

### Post by thhp on 2006-09-22
Hum. I don't seem to have an 'admin' group. The closest thing I have is 'adm', and we're both a member of that:

```

thhp@orangutang:~$ cat /etc/group | grep admin
lpadmin:x:104:thhp,flo
thhp@orangutang:~$ cat /etc/group | grep ^a
adm:x:4:thhp,flo
audio:x:29:thhp,flo

```

However, it occurs to me that maybe 'flo' needs to have sudo priviledges? Perhaps Gnome is cunning enough to work this out... I'll try adding 'flo' to sudoers and see what that achieves.


Thanks,

T

---

### Post by thhp on 2006-09-22
Nope, no dice. Both users are now in /etc/sudoers with the same priviledges, and I can use sudo to get root priviledges as both users... but only one user can shut down the machine.

Any further suggestions?


Thanks,


T

---

### Post by ayoli on 2006-09-22
weird, i have an admin group (created by the install, not by me) which contains my first user, i add to it my second user, and i have a line in /etc/sudoers which allows all users of admin group to grant root rights.
and that works.

---

### Post by thhp on 2006-09-22
Hum, that is a bit odd. Oh well... I'll keep on poking around... 

Thanks for your help anyway :)


T

---

