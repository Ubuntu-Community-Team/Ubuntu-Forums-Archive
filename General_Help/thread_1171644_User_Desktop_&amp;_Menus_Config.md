---
title: "User Desktop &amp; Menus Config"
date: 2009-05-27
forum: General Help
---

### Post by measekite on 2009-05-27
Asssumption:

You will have 3 or 4 users.
UserOne
UserTwo
UserThree
UserFour

You perform a clean install with only one User.  That UserName will be UserRoot.  UserRoot has full control.

UserOne (not created) as yet will have admin control but not full root access.

Question:

1. How can UserRoot create and configure a standard desktop, a modified menu system, colors, preferences and other configuration items so that when each new user is created they automatically get this Standard Configuration?

2.  How can you place each of these users home folders on a partition separate from the OS.  Let say you call the partition "partHome".  What configuration files do you need to edit and how?  After you do this will each newly created users have their home folder on partHome or do you have to move them there?

---

### Post by CatKiller on 2009-05-28
> **measekite said:**
> 
You perform a clean install with only one User.  That UserName will be UserRoot.  UserRoot has full control.

Not quite. UserRoot (or whatever you call it; just don't call it *root* or *admin*, or you're looking at a whole lot of unnecessary pain) will have admin access, meaning that they can use *sudo* to temporarily become root. See, for example, [this page]("https://help.ubuntu.com/community/RootSudo").

> 
UserOne (not created) as yet will have admin control but not full root access.


Control of which users get to do what using sudo is controlled by entries in the /etc/sudoers file.

> 
Question:

1. How can UserRoot create and configure a standard desktop, a modified menu system, colors, preferences and other configuration items so that when each new user is created they automatically get this Standard Configuration?


The folder that it used as a template for a new user's Home folder is /etc/skel. You can put configuration files in here to have them applied to all new users. There may be other default locations for new configuration files that I can't recall at the moment.

> 
2.  How can you place each of these users home folders on a partition separate from the OS.  Let say you call the partition "partHome".  What configuration files do you need to edit and how?  After you do this will each newly created users have their home folder on partHome or do you have to move them there?

If you create a /home partition during the install process, any new directories that are to be created under /home, for example a new user's Home folder, will be created on that partition. If you want to change an existing installation so that /home is a separate partition then you need to edit /etc/fstab to tell the system to mount a given partition at a given location and copy the files you want there from the old location to the new one. [Here]("http://www.psychocats.net/ubuntu/separatehome") is a guide.

---

