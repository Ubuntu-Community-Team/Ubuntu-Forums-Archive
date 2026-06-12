---
title: "Enemy Territory Issues"
date: 2005-05-28
forum: Gaming &amp; Leisure
---

### Post by wh33t on 2005-05-28
Ummm... how do I install this game? I downloaded a 260mb et-linux-2.60.x86.run file and when I try to do a ./et-linux-2.60.x86.run file it says: 

```
wh33t@wh33tbox:~$ ./et-linux-2.60.x86.run
bash: ./et-linux-2.60.x86.run: Permission denied
```

When I do a sudo ./et-linux-2.60.x86.run it says:

```
wh33t@wh33tbox:~$ sudo ./et-linux-2.60.x86.run
Password:
sudo: ./et-linux-2.60.x86.run: command not found
```

I cant even find on the Enemy Territory the install instructions, so I was just guessing with the dot slash run manuever. But if you guys could be of any help that would totally rock.

---

### Post by matid on 2005-05-28
```
sudo sh et-linux-2.60.x86.run
```
BTW. Make sure the partition you're running it on allows you to execute files.

---

### Post by wh33t on 2005-05-28
Thank you. That worked.

---

