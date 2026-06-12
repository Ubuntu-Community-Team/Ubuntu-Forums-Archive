---
title: "Problem with Nautilus"
date: 2008-03-10
forum: Desktop Environments
---

### Post by menotu3169 on 2008-03-10
Hi, I've got a problem with Nautilus, I think this is the right place to post.  I've searched the forum but haven't found anthing matching my problem so . . .here it goes.

After I've been using nautilus for a while to browse and edit files(delete/rename/etc) it stops working on me. All of a sudden it will not open files, it displays the error ```
The folder contents could not be displayed.
``` if I try to go to another folder, and if I select a file, it won't show the proper icon, it will just show a blank square. If I close the window and try to open it again, nothing happens. The only way I've found to fix it, is to restart nautilus completely  through system monitor.  

It appears to happen randomly. I might be able to use it for an hour, or it might crash after 10 minutes. Sometimes it will happen when I try to rename a file, or sometimes if I try to open one. 

I'm using Ubuntu 7.10 Gutsy Gibbon. I'm not sure what other information you might need. Any help is greatly appreciated.

---

### Post by x1a4 on 2008-03-10
This looks like a permission problem not a Nautilus problem.  Check ownership/permissions of the directories/files you are trying to access, and modify them accordingly.

Right-click on the directory/file you wish to check, click the 'Permissions' tab.  If the ownership/permissions are incorrect and you have no permission to change them, run Nautilus with root priviledges: ```
gksudo nautilus
``` .

---

### Post by menotu3169 on 2008-03-10
Thanks for the reply. :)

I checked the permissions for both files and folders, and they all seem to be fine.

For folders, the permissions are 770 : ROOT and PLUGDEV both have permission to Create and Delete files, OTHERs have no permissions.

And it's the same for files, 770 : ROOT and PLUGDEV have Read and Write permissions while OTHERS have none.

The thing that doesn't make sense to me, is if it IS a permissions problem, why would I be able to edit, delete or rename files at all?

---

### Post by x1a4 on 2008-03-11
Check to see if you can access the directories properly from a terminal, and set the execute bit for all users  Also, remove Nautilus configuration files and reinstall it, and see if that helps.

---

### Post by x1a4 on 2008-03-11
Check to see if you can access the directories properly from a terminal, and set the execute bit for all users.  Also, remove Nautilus configuration files and reinstall it, and see if that helps.

---

