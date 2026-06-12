---
title: "User &amp; Directory Permissions"
date: 2009-04-28
forum: General Help
---

### Post by pavsid on 2009-04-28
Hi, i think i still have trouble understanding permissions and how to set them.

Anyway, i recently set up an FTP server on my home machine (Ubuntu Jaunty) and created a user 'user2' who is part of the group 'ftpusers'.  I set the home directory of user2 as a drive on the machine 'DATA'.  I set the ownership of that drive as root with permissions 777 so that when i login via FTP i can still make changes.

Now, when i log in by FTP although i can change and amend existing files or folders, if i create any then when i am logged in at home as myself then i can't change those files (because the owner is user2).

What is the way round this? 

Thanks

---

### Post by pavsid on 2009-04-29
Would this work?

Creating another 'home' directory somewhere else and then mapping the required drive (DATA) to that folder?

If so, how do you map a drive to that folder? And would any newly created folders still be owned by the current user?  

In fact can't you set the default permission for a user with umask or something? How does that work, i've looked for a guide but can;t really find anything

---

