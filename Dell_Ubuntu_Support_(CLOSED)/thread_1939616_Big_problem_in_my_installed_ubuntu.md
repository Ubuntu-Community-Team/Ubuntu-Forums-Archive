---
title: "Big problem in my installed ubuntu"
date: 2012-03-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Janiche on 2012-03-12
well, yesterday I installed Ubuntu 11.10 in my dell inspiron 1420.
the problem is: the live CD recognizes the hardware and works perfect, but yn the installed version, nothing works. no wifi, no lan, the options Users accounts, aditional drivers and repositories wn't launch.

and I don't know what can I do.

please help me

---

### Post by varunendra on 2012-03-12
> **Janiche said:**
> the installed version, nothing works. no wifi, no lan, the options Users accounts, aditional drivers and repositories wn't launch.
I couldn't understand the 'User accounts' part of your problem. Please provide the details of the problem(s).

Rest of whatever you mentioned seem to be networking related (repos/additional drivers won't launch until you get connected to internet at least once). Accordingly, please post the outputs of:
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
```
While posting the outputs, click on **#** at the top of the edit box to generate [ code]..[ /code] tags, then copy-paste the output code in-between those tags.

---

### Post by Janiche on 2012-03-12
I solved the problem.

Just reinstall ubuntu in the same particion, maybe was a bad installation.

thank you for the given time

---

