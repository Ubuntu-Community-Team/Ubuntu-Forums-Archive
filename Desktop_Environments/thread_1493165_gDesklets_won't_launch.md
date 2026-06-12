---
title: "gDesklets won't launch"
date: 2010-05-25
forum: Desktop Environments
---

### Post by xcrunner78 on 2010-05-25
Since I upgraded to 10.04, I went to launch gDesklets, and it will not launch.  I looks like it wants to, spinning cursor and bar down in the task bar panel, but then it disappears.  Suggestions?

---

### Post by Zemblan on 2010-05-25
Try starting it from a terminal, and see what errors that produces.

---

### Post by xcrunner78 on 2010-05-25
How would I do that..launch it from the terminal?

---

### Post by Zemblan on 2010-05-26
Applications -> Accessories -> Terminal

In the window that opens type 'gdesklets', it will probably print out some information, if it fails to start it will produce an error which may help work out why it has failed.

EDIT: It's not working for me either. It appears that there is a bug to do with the wrong version of python:

[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/569714](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/569714)

Some solutions are offered there.

---

### Post by mister_p_1998 on 2010-05-27
you've got to roll back to the previous version (0.3.6.1.3)
and DONT update it!
see here:
[http://ubuntuforums.org/showthread.php?t=1454324](http://ubuntuforums.org/showthread.php?t=1454324)
Steve

---

### Post by xcrunner78 on 2010-05-27
hmmmm....I already did a complete remove through synaptic.  I got tired of messing around with it.  Is there a way that I could get it back, to the older version?

---

