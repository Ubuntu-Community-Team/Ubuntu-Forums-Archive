---
title: "I think I took myself out of admin group and now I can't use sudo"
date: 2009-03-05
forum: General Help
---

### Post by Uzi304 on 2009-03-05
Ok so to try and fix my XMMS's problem of [B]"please check that:
your sound card is configured properly
you have the correct output plugin selected
no other program is blocking the soundcard"[/B]so to fix it, one of the solutions suggested was ```
usermod -G audio 'normal_username
```and now I can't use the sudo command because it says **username  is not in the sudoers file.  This incident will be reported.**

---

### Post by kuja on 2009-03-05
1)reboot with the recovery mode option at grub
2)choose root shell when given the option
3)type in adduser yourusername admin
4)type in exit and resume normal boot

---

### Post by Uzi304 on 2009-03-05
Ah thanks! It's good now but could you explain why this happened in the first place?

---

### Post by snl2587 on 2009-03-05
Yes. From man usermod:

-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with the -g option. **If the user is currently a member of a group which is not listed, the user will be removed from the group.** This behaviour can be changed via the -a option, which appends the user to the current supplementary group list.


Should have used -a

---

