---
title: "files/folders permissions is confussing me"
date: 2005-10-30
forum: Desktop Environments
---

### Post by OBnascar on 2005-10-30
I just installed ubuntu 5.10 on a second computer and my wireless PCI adapter connection is working perfectly.

But, unlike my first computer, I am unable to do anything with my files and folders. How can a install on one computer be different than another ? 

I have tried the following from ubuntu documentation:

How do I change files/folders permissions?
   1. Right click the file or folder. Select the Properties option. Select the Permissions tab. For the Owner, Group and Others check/uncheck the Read, Write, Execute options to set or unset permissions.	

How do I change files/folders ownership?
   1. sudo chown system_username /location_of_files_or_folders

How do I change files/folders group ownership?
   1. sudo chgrp system_groupname /location_of_files_or_folders

None of these work for me on my second computer !
Does anyone have any fresh idea's ?
If more info is needed let me know please.

Any comments, suggestions, and opinions are welcome !

---

### Post by ofek on 2005-10-30
chmod 755 /locationoffiles/folder might solve the problem however 755 lets the root full premission and others only read and execution premission they cannot write if u want read write for all users (not recomended) u can try chmod 777 instead of chmod 755.
*of course that b4 all the commands above should come sudo.

---

### Post by matthewv on 2005-10-30
[QUOTE=ofek]chmod 755 /locationoffiles/folder might solve the problem however 755 lets the root full premission and others only read and execution premission they cannot write if u want read write for all users (not recomended) u can try chmod 777 instead of chmod 755.
*of course that b4 all the commands above should come sudo.[/QUOTE]
Many files on a linux install are not meant to be touched, which could be why you can't change them. The only place where you should have full access is your home folder.

---

### Post by OBnascar on 2005-10-30
[QUOTE=matthewv]Many files on a linux install are not meant to be touched, which could be why you can't change them. The only place where you should have full access is your home folder.[/QUOTE]

Ok, thanks matthewv

What I actually was trying to do was, I burned My Documents, Firefox bookmarks.html, Thunderbird mail, and Thunderbird abook.mab files on a CD from my first computer. and was going to copy them to my second computer.

I was able to do it by dragging them from the CD browser to the desktop of my second computer, then there I was able to check read, write, and exe. Next I deleted the files to be replaced in my second computer and replaced them with the ones from my desktop. There may be a better way but this got the job done for me. One should be able to just copy over the existing files but that does not always seem to work for some reason.

---

### Post by Zwack on 2005-10-30
If your user doesn't have the same user ID on both machines you could have problems...  It has the same name, but a different uid... It looks the same until you actually try to use it.

Unix goes by the UID, not the user name most of the time.  So, oracle could have UID 2003 and UID 2005 (on different systems, or even on the same system)...  They would both be called oracle but they are two distinct users.

Worse, you could have different entries in the /etc/passwd file so that you have three different names, two different UIDs and a lot of confusion as to who is what...
```

user1:x:1000:1000:User One,,,:/home/user1:/bin/bash
user2:x:1001:1001:User Two,,,:/home/user2:/bin/bash
user3:x:1000:1000:User Three,,,:/home/user1:/bin/bash
user3:x:1001:1001:User Three,,,:/home/user2:/bin/bash
```

In this case, we have user1, user2, user3 and user3.  user3 is in one instance the same as user1, and in the other is the same as user2.

So, what happens if user3 logs in?  They appear to be the same as user1.  The UID is the same in the first entry that matches, so user1 has effectively logged in.

If the two user3 lines were swapped then it would work as user3.

More confusing still is :
```
user1:x:1000:1000:User One,,,:/home/user1:/bin/bash
user3:x:1000:1000:User Three,,,:/home/user1:/bin/bash
user3:x:1001:1001:User Three,,,:/home/user2:/bin/bash
user2:x:1001:1001:User Two,,,:/home/user2:/bin/bash
```

Now, if user2 logs in they would appear to be user3, but if user3 logs in they would actually appear to be user 1.  The system takes the first line that matches in the passwd file.  If you consider that these entries could be spelled out throughout a several thousand entry password file you can see why it might be confusing if this  actually happened.

Z.

---

### Post by poptones on 2005-10-30
I think you got it right but I don't see a clear resolution there to the problem.

Try this: chown -R myusername:myusername /these/folders

Note the "username:username" with a colon between. That will set both the userid and the groupid of the files and should fix your problem.

---

### Post by OBnascar on 2005-10-31
[QUOTE=poptones]I think you got it right but I don't see a clear resolution there to the problem.

Try this: chown -R myusername:myusername /these/folders

Note the "username:username" with a colon between. That will set both the userid and the groupid of the files and should fix your problem.[/QUOTE]

Hi poptones, that does work, I will add it to my Commands Library

---

