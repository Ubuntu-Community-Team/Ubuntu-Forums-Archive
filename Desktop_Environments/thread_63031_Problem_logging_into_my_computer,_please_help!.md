---
title: "Problem logging into my computer, please help!"
date: 2005-09-06
forum: Desktop Environments
---

### Post by GregDonohoe on 2005-09-06
When I try to login to my computer I get this message : 

"GDM could not write to your authentication file. This could mean that you are out of disk space or that your home directory could not be opened  for writing. In any case, it is not possible to login. Please contact your system administrator. "

How can I solve this problem?

Thanks in advance.

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=GregDonohoe]When I try to login to my computer I get this message : 

"GDM could not write to your authentication file. This could mean that you are out of disk space or that your home directory could not be opened  for writing. In any case, it is not possible to login. Please contact your system administrator. "

How can I solve this problem?

Thanks in advance.[/QUOTE]
Well, are you out of disk space?  Do permissions on your home directory seem to be set to allow you to have access?  You can jump over to a console with CTRL-ALT-F1 and log in there so you can have a look around.  Also, does this only happen with your user?  Maybe you can log into another user and investigate the problem that way.

---

### Post by GregDonohoe on 2005-09-06
Ok, the partition is full, so can you tell me what command to use to delete files. Thanks.

---

### Post by seethru on 2005-09-06
[QUOTE=GregDonohoe]Ok, the partition is full, so can you tell me what command to use to delete files. Thanks.[/QUOTE]
 the command is rm, or sudo rm and if it's an entire directoy use the flags -rf

---

### Post by GregDonohoe on 2005-09-06
Thanks alot, that's solved my problem!

---

### Post by xe1ufo on 2007-09-29
I had exactly the same problem, and your solution was exactly right!!!! Thanks a million!!!!:popcorn:

---

