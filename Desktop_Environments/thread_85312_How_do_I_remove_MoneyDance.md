---
title: "How do I remove MoneyDance?"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Darrin on 2005-11-02
I installed it in /usr/local/bin. I wish to remove it. Is it sudo rm moneydance? not sure what steps to take. I dont want to try it unless Im sure I wont mess it up.

---

### Post by Kyral on 2005-11-02
Lemme guess, a source thing that wasn't in the repos?

Those are a pain to get out. Wiping out the dir that its installed in would get rid of most of the files though.

---

### Post by Darrin on 2005-11-02
[QUOTE=Kyral]Lemme guess, a source thing that wasn't in the repos?

Those are a pain to get out. Wiping out the dir that its installed in would get rid of most of the files though.[/QUOTE]

Correct it wasnt in the repos. I noticed in moneydance there is an icon labeled Money dance uninstaller, but I currently dont have permissions. Should I try to launch that?

---

### Post by Kyral on 2005-11-02
Find out where it lives in the filesystem (Right click -> Properties) and go to a terminal and sudo the command :D

---

### Post by Darrin on 2005-11-02
[QUOTE=Kyral]Find out where it lives in the filesystem (Right click -> Properties) and go to a terminal and sudo the command :D[/QUOTE]

Thanks. The following command worked. It be gone ;) 
```
sudo /usr/local/moneydance/uninstall

```

---

### Post by arak on 2007-02-09
I removed Moneydance and have the following message every time I boot:

could not load icon

Details: Icon '/home/walt/moneydance/.install4j/Moneydance.png' not found

How do I get rid of this?  The folder not longer exists.

---

