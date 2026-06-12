---
title: "Folder permission limited to 1 user only"
date: 2006-07-14
forum: Desktop Environments
---

### Post by driesel on 2006-07-14
Hi,

Using a HOWTO I configured a FTP-client user, which has a home directory in /home/FTP-shared.
I cannot log into GNOME using this user, because it has no real functionality besides the necessary folder access to this home directory.

Now, I've made myself another user account, adminftp, to manage all downloads and uploads.  So it must have ALL access to the /home/FTP-shared (includes download and upload folder) using this account.
How can I configure this using a terminal, since I can't configure it that way using the GUI
AGAIN: it is important that only 'adminftp' has all rights to these folders.


greetings,
driesel

---

### Post by JayCnrs on 2006-07-15
You can change the permissions on the folder, you will need to create a group called FTP-client. Once this group is created you can then change the permission from a terminal such as, depending on the type of access you want the FTP-client to have I am assuming Read only. So once you have created the group ensure that the user FTP-client is part of the FTP-client group now set the permission on the folder and all files inside to :

chown -R adminftp:FTP-client /home/FTP-shared
chmod -R 740 /home/FTP-shared

This will cause all permissions on the folder and the files contained within to be:

adminftp - Full read/write/execute 
FTP-client group - Read only access

With chmod 4 = read, 2 = write, 1 = execute 

Hope this helps

---

### Post by driesel on 2006-07-15
Okay,

Let's see.
So with your howto I can have this:

*ownership of FTP-shared changed to adminftp user
*other groupmembers of e.g. 'FTP users' besides adminftp only read access.

That's almost what I want, but I want FTP clients to be able to upload, so the must be write permission for the FTP-shared/upload folder (without overwriting).
How can I arrange this?

I think we're almost there ;).

greetings,
driesel

---

