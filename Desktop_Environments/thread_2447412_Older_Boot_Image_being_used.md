---
title: "Older Boot Image being used"
date: 2020-07-18
forum: Desktop Environments
---

### Post by daithi_dearg on 2020-07-18
Hello,

I think along time in the distant past I made a change to revert to an older boot image and I am remaining on this after the upgrades.

I have images as follows:
```
-rw-r--r-- 1 root root 217018 Oct 23  2018 /boot/config-4.15.0-39-generic
-rw-r--r-- 1 root root 237753 Jun 19 10:56 /boot/config-5.4.0-39-generic
-rw-r--r-- 1 root root 237773 Jun 22 21:59 /boot/config-5.4.0-40-generic
```

It uses the 4.15.0-39 Image. Any suggestions for changing this?

Regards,
David

---

### Post by Bashing-om on 2020-07-18
daithi_dearg; Hey hey -

> 
I think along time in the distant past I made a change 


Post back:
```

cat /etc/default/grub
uname -r
lsb_release -a

```
and show us what there is to work with:
```

ls -al /
ls -al /boot/

```

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by daithi_dearg on 2020-07-25
Changed:
GRUB_DEFAULT=0

Was originally:
GRUB_DEFAULT='gnulinux-advanced-f2d3ef71-2ac0-4c8c-b7be-07494164bf85>gnulinux-4.15.0-39-generic-advanced-f2d3ef71-2ac0-4c8c-b7be-07494164bf85'

No longer seeing the message about the boot image when I'm booting up so think I should be good. Appreciate the inputs

---

### Post by Bashing-om on 2020-07-25
daithi_dearg; Great :)

Looks sane to me.

As this issues has resolution ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

