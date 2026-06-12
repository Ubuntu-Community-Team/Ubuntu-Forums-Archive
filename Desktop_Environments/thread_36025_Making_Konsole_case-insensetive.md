---
title: "Making Konsole case-insensetive"
date: 2005-05-21
forum: Desktop Environments
---

### Post by SGC on 2005-05-21
I remember when I used simpleyMepis that Konsole was case-insensitive so typing

**cd FOLDER_NAME** give you the same results as **cd folder_name**

How to do the same in Kubuntu?

---

### Post by stevenyu on 2005-05-21
Unh, are you sure, when Linus wrote the kernel he imaged following MINIX and UNIX, and both OS have a history of case-sensetive in the terminal.

---

### Post by SGC on 2005-05-21
[QUOTE=stevenyu]Unh, are you sure, when Linus wrote the kernel he imaged following MINIX and UNIX, and both OS have a history of case-sensetive in the terminal.[/QUOTE]
 I know , I was suprised when I found out about this feature.

---

### Post by Firetech on 2005-05-22
It probably has to do with which shell Mepis uses, or the config of the shell, because it isn't Konsole that does the auto-completion.
If you have the ability to run Mepis again, fire up a Konsole and run "echo $SHELL", then check the manpage for that shell (omit the "/bin/"-part) using man [name-here], to find out where it has it's config.

---

### Post by SGC on 2005-05-23
[QUOTE=Firetech]It probably has to do with which shell Mepis uses, or the config of the shell, because it isn't Konsole that does the auto-completion.
If you have the ability to run Mepis again, fire up a Konsole and run "echo $SHELL", then check the manpage for that shell (omit the "/bin/"-part) using man [name-here], to find out where it has it's config.[/QUOTE]
 I uninstalled mepis along time ago, and I lost the Live cd , But thanks for your help.

---

### Post by sancho on 2005-05-24
I haven't worked with Mepis much but when i saw this post it made me curious...

I booted off simply mepis 3.3 disc.   I however could not get the actions you are talking about to work.  Tab completeion would not work neither would typing the case wrong by hand. I do know they are using bash though, at least on the live cd anhow.  

Maybe its different when you do a full install?

---

### Post by SGC on 2005-05-24
I discovered this feature in mepis after installing kde 3.4, so maybe it does have to do with this or other program I installed.

---

