---
title: "How reactive a user account?"
date: 2013-12-30
forum: Desktop Environments
---

### Post by ruwan2 on 2013-12-30
Hi,
My previous Ubuntu 12.10 had a separate home partition with user Jeff. I reinstalled Ubuntu 12.04 hoping to reuse home directory data/content. One error was made that I inputed another user name: Robert. I find that I cannot reactive Jeff now. When I put the below commands, it warns that the old directory are not associated with the new account any morre. Do you have solutions besides to backup those data out?

Thanks,




[COLOR=#000080]robert@M5100:~$ sudo adduser jeff
Adding user `jeff' ...
Adding new group `jeff' (1001) ...
Adding new user `jeff' (1001) with group `jeff' ...
The home directory `/home/jeff' already exists. Not copying from `/etc/skel'.
adduser: [/COLOR][COLOR=#a52a2a]Warning: The home directory `/home/jeff' does not belong to the user that you are currently creating.[/COLOR][COLOR=#000080]
Enter new UNIX password: 
[/COLOR]

---

### Post by ian-weisser on 2013-12-30
> **ruwan2 said:**
> [COLOR=#000080]robert@M5100:~$ sudo adduser jeff
Adding user `jeff' ...
Adding new group `jeff' (1001) ...
Adding new user `jeff' (1001) with group `jeff' ...
The home directory `/home/jeff' already exists. Not copying from `/etc/skel'.
adduser: [/COLOR][COLOR=#a52a2a]Warning: The home directory `/home/jeff' does not belong to the user that you are currently creating.[/COLOR][COLOR=#000080]
Enter new UNIX password: 
[/COLOR]

User permissions are based on the UID number, not the name. The name is simply a human-readable label.
"jeff"s new UID is 1001. The old one was probably 1000 - user UIDs start at 1000 and increment upward.
Specify a UID with adduser's --uid flag. See man adduser.

Or simply copy old-jeff's /home to new-jeff's /home. No backup required.

---

