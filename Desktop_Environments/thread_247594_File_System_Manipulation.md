---
title: "File System Manipulation"
date: 2006-08-30
forum: Desktop Environments
---

### Post by grengabuntu on 2006-08-30
Hi folks,

I'm brand new to Ubuntu and Linux. So far, I've had a successful install and I've been able to network my printer from my Ubuntu box (with 2 XP laptops).

I've been fiddling around trying to do the following tasks, but really need some direction. Here goes...

1.) I would like to create new directories for my various projects in the /home folder (/home/proj1, home/proj2, home/proj3, etc..). How can I do this and establish permissions so that all users can access these folders? Is this a good approach for organizing my projects?

2.) How could I go about sharing these new folders so that my laptops can access them?

3.) How can I automatically set up Ubuntu to do nightly backups on each folder? I would like to copy all contents to an external USB HDD that already works great with Ubuntu.

Anyway, thanks for any direction!

---

### Post by CatKiller on 2006-08-31
> 1.) I would like to create new directories for my various projects in the /home folder (/home/proj1, home/proj2, home/proj3, etc..). How can I do this and establish permissions so that all users can access these folders? Is this a good approach for organizing my projects?I don't know about the other bits - I'm quite new to Linux myself. But I'd be inclined to make a new directory somewhere else /projects, for example, and make that read/writeable to everyone and leave your home folder permissions as they are. Haven't tried sharing folders over the network, but I understand that it's Samba you'll need to share with Windows computers. I believe it's fairly intuitive from the little I've read.

---

### Post by grengabuntu on 2006-08-31
Great advice. I can create a projects folder outside of home. I have Samba installed, but haven't used it yet. I also suspect that I'll need a kron job for my backups.

How can I set folder permissions? Do I need to do it through the terminal?

Thanks again everyone...

---

### Post by dumbo on 2006-08-31
> **grengabuntu said:**
> Great advice. I can create a projects folder outside of home. I have Samba installed, but haven't used it yet. I also suspect that I'll need a kron job for my backups.

How can I set folder permissions? Do I need to do it through the terminal?

Thanks again everyone...

Folder permissions can be set from the command line, or nautilus.

Basically, you'll need to:
0 [optional] create a group (e.g. 'projects', and add all the users to it).  You can do this in the users and groups manager - under the groups tab.

1 Create the directory.  Easiest to do this from the command line e.g. "sudo mkdir /projects".

2 Set the owner/group on that directory.  I'd recommend 'sudo chown username:projects /projects'.  [replace 'username' with your username]

3 Browse to the root aka '/' folder in nautilus and highlight the projects folder, right click and select 'properties'. select the permissions tab.  (if you created the group in step 0) Check 'group write' and 'set group ID'.  If you didn't create the group, then grant 'others' 'read/write/execute' access.

---

Ideally new files/folders within 'projects' would by default have group read/write access - but I don't know any way to force that :(.

---

### Post by grengabuntu on 2006-09-02
Thanks so far for the great advice. So far so good. I have my folders set up and permissions are set. I am still looking for these items:

> **grengabuntu said:**
> 
2.) How could I go about sharing these new folders so that my laptops can access them?

3.) How can I automatically set up Ubuntu to do nightly backups on each folder? I would like to copy all contents to an external USB HDD that already works great with Ubuntu.


I think #2 has to do with Samba and #3 with Keep. Any thoughts?

---

