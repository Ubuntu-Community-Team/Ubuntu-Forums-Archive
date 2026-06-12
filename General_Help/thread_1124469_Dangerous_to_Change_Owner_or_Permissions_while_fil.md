---
title: "Dangerous to Change Owner or Permissions while file is being used?"
date: 2009-04-13
forum: General Help
---

### Post by Buggin1965 on 2009-04-13
Hello,
I have search, but cannot find an answer to the question: 
Is it dangerous to change the owner, group, or permissions of a file that is currently in use?

I have a samba file server that has a waterfall permission structure with four user account access levels:
 

  OWNER  : Group Members
  Super   :   Super
    |
   \|/
  Project :  Super, Project
    |
   \|/
  Common  : Super, Project, Common
    |
   \|/
  Share   : nogroup, super, project, common

All permissions are set to 0770 except "share" has 0777
Super, project, and common have passwords.
Share does not.

The users are having problems moving files from one level. And Files or folders created by a higher level user are read only for lower level users.

I created a simple bash script that is run by crontab every 5 minutes that changes all of the folders and file permissions.

If someone has a database or file open, and the owner changes, could the file become corrupted? or is there no danger?

Thank you.

---

### Post by defaultusername on 2009-04-13
Buggin1965,

Executing a simply chmod/chown/chgrp isn't going to corrupt a file. The cron job is a really bad idea. Have you looked into chown/chgrp?

Add users to their privileged supergroups and change the group ownership-levels recursively on directories/files. "Common" is a set of users, a group. Unix has a command to change group ownership, chgrp. Users have a set of groups to which they are members. Project developers, in your example, would belong to Share, Common, and Project and be excluded from the Super group. Super would be a member of all the above. By assigning group ownership to different subdirectories, you can be confident that users of that group can r/w/x in their assigned part of the directory tree. Also, 0774 is safer than 0777 allowing only members of appropriate group write privileges.

---

