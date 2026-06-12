---
title: "Sharing files between local users"
date: 2006-10-06
forum: Desktop Environments
---

### Post by lupin on 2006-10-06
Hi,

it looks to me like a very simple question, but I can't find an easy answer or solution.

I simply want to have a directory on my Linux installation that can be used by all local users, and that contains only shared files. I'm not talking about sharing those files with other computers.

Yes, I know I can set 777 permissions to that dir, but if I move a file there, it keeps its own permissions. Is there a way to have all files available to everyone? Should I use a FAT32 partition for that? :( 

Thanks in advance for any suggestion.

---

### Post by leetcharmer on 2007-05-26
I have the same question.  Any answers?

---

### Post by DW5 on 2007-06-08
I would like to do that, too.  In my particular case, I want to save all my family's digital photos to a common folder and allow all my family members to access (view, copy, edit) those files.  I have done the following to accomplish it.

1) set up a group called pictures using System|Administration|Users and Groups.
2) added all users to the group
3) from the terminal used chgrp command to change the group of every file in the Pictures directory to pictures
```
sudo chgrp -hR pictures /home/Pictures
```
4) I then used sudo to start nautilus and changed the permissions of each subfolder to allow the picture group to read and write files (I know there is a command line to do this, but I was too lazy to poke around and find it).  If I had been thinking, I would not have created any subfolders and just dumped all the pictures into the one big folder, that would have only required one change...but there's that lack of prior planning caused by experimental mindset.
5) I think that's done it for the existing files.  However, I suspect I will have to run the command 
```
sudo chgrp -hR pictures /home/Pictures
``` every time I upload more pictures to my folder since I think there permissions will be set differently (hope I'm wrong).

DW

---

