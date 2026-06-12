---
title: "Temp files location; can it be changed?"
date: 2005-08-10
forum: Desktop Environments
---

### Post by alquimista on 2005-08-10
Hi,
When I first installed the Kubuntu partition I though It'd be for testing  and learning Linux, yet step by step I'm adopting it as my main OS. The problem is that I initially assigned 5Gb of disk partition and now I'm at 94% of its use; many temp files for Ark and Oppen Office can't be created and apps. simply stop working. Is there a way to change the path of temp files to another partition? I have a data partition (FAT32 21Gb) shared with Winwhere I can locate temp files. The current temp directory semms to be "//tmp/kde-user"

Thanx !
Guillermo

---

### Post by tonysathre on 2005-08-10
[QUOTE=alquimista]Hi,
When I first installed the Kubuntu partition I though It'd be for testing  and learning Linux, yet step by step I'm adopting it as my main OS. The problem is that I initially assigned 5Gb of disk partition and now I'm at 94% of its use; many temp files for Ark and Oppen Office can't be created and apps. simply stop working. Is there a way to change the path of temp files to another partition? I have a data partition (FAT32 21Gb) shared with Winwhere I can locate temp files. The current temp directory semms to be "//tmp/kde-user"

Thanx !
Guillermo[/QUOTE]
 yes...when you install create a partition and give it the location /tmp

---

### Post by alquimista on 2005-08-10
Thank you;

Is it possible to assign this temp whithout reinstalling all Kubuntu? is it possible to configure something to have it pointing to my big FAT32 partition?


Guillermo

---

### Post by cwaldbieser on 2005-08-10
[QUOTE=alquimista]Thank you;

Is it possible to assign this temp whithout reinstalling all Kubuntu? is it possible to configure something to have it pointing to my big FAT32 partition?

Guillermo[/QUOTE]
You should be able to change your /etc/fstab entries to mount /tmp on the FAT32 partition.

---

