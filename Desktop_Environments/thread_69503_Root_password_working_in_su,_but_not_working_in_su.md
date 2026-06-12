---
title: "Root password working in su, but not working in sudo or kdesu"
date: 2005-09-27
forum: Desktop Environments
---

### Post by TeePOG on 2005-09-27
Hi list

This is almost my first post, so be gentle.

I installed my edubuntu system in expert mode, because I didn't want it to setup my home machine as a LTSP server. During the installation, it prompted me for a root password.

Trouble is, now I can only use su from command prompt. Root password works for this. Neither kdesu nor sudo, however, accepts my root password OR my normal account's password.

Please tell me what I did wrong.

Arno

---

### Post by Tiede on 2005-09-27
in a terminal, type ```
 sudo passwd root 
``` to set a different root password.

---

### Post by TeePOG on 2005-09-27
yes, that might work... except sudo ***does not accept my _correct_ root password!***

Sigh.

What can I do, running in normal su root, to fix it?

---

### Post by Tiede on 2005-09-27
Oups, sorry for my (dumb) post :-D
Well, you couold try it out with su... maybe that'll work. Otherwise, try it out from the command line.

---

### Post by TeePOG on 2005-09-27
[QUOTE=Tiede]Oups, sorry for my (dumb) post :-D
Well, you couold try it out with su... maybe that'll work. Otherwise, try it out from the command line.[/QUOTE]

Didn't mean it was dumb... I thought I didn't explain properly. I know how frustrating that is for support people.

What, exactly, should I try out from the command line?

Arno

---

### Post by Tiede on 2005-09-27
well, from the shell prompt, try ```
sudo passwd root
```, if it does not work - and I know it won't -, try ```
su passwd root
```.

---

### Post by Tiede on 2005-09-27
and just a reminder, the sudo password in NOT the root's password, it's yours. I hope you did not mix them. ;)

---

### Post by Mustard on 2005-09-27
When you get sudo working again, you can disable the root account with

```
sudo passwd -l root
```

If you want to return to the standard way Ubuntu operates from default install.

---

### Post by TeePOG on 2005-09-27
[QUOTE=Tiede]and just a reminder, the sudo password in NOT the root's password, it's yours. I hope you did not mix them. ;)[/QUOTE]

OK, root password succesfully changed, although that wasn't the problem.

I did not mix them, no... it just doesn't want to accept my normal user login as a sudo/kdesu password.

Could it be that my normal login is, for some reason, not on the sudoers list? How do I check , and how do I fix it? All needs to be done from the console, as root su.

Thanks for the help so far.

---

### Post by TeePOG on 2005-09-27
[QUOTE=TeePOG]Could it be that my normal login is, for some reason, not on the sudoers list? How do I check , and how do I fix it? All needs to be done from the console, as root su.[/QUOTE]

I figured it out... *wry grin*

As su root,

```
nano /etc/sudoers
```

Add the line <username> ALL=(ALL) ALL at the end

Save [Ctrl-X] and exit.

Exit root, then sudo normally.

Thanks for the guidance.

Arno

---

