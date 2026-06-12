---
title: "Two xorg-instances wasting my RAM"
date: 2008-05-30
forum: Desktop Environments
---

### Post by nic-stange on 2008-05-30
Hi everybody,
I just recognized two instances of Xorg running on my new hardy and wasting my memory (each needs 14%). One of the has 0.00:0 CPU time. See attached ps.txt.
For hierarchy, see pstree.txt
For which files each of the ones has opened, see the lsof.pid.txt
For my xorg.conf see xorg.conf.txt

This lost memory is really annoying for me as there isn't so much on my laptop avaiable.

Thanky you very much!

Nicolai

---

### Post by nic-stange on 2008-05-30
And the relevant logs (veriefied via ls -l: there are no others assigned to my current running session).

Nicolai

---

### Post by Fire_Chief on 2008-08-04
I have the same issue happening. It seems rather strange but I don't want to kill it off for risk of breaking something.

---

### Post by dje on 2008-08-04
me too, let me guess you both have ati graphics cards and are using the proprietary driver?

dje

---

### Post by nic-stange on 2008-08-04
Yes: ATI-card, properitary driver.
But after a bit of further investigation, I don't think that the ressources are really physically allocated for two times. It seems that one of the processes is just a sleeping (thus it's not using CPU) fork of the other.
So it's a bit non-straightforward, but it doesn't really matter.
And for that: I'll mark this thread 'resolved' as soon as I get out how to do it ;)

---

### Post by mali2297 on 2008-08-04
Yes, it is a known bug in the ATI proprietary driver.

To mark the thread as solved, look in the [color=red]Thread Tools[/color] menu above.

---

