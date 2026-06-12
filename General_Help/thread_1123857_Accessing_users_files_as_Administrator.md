---
title: "Accessing users files as Administrator"
date: 2009-04-12
forum: General Help
---

### Post by ayastona on 2009-04-12
I have set up a new user for my brother so he can use my computer and learn linux!

I set up his account under his name and started configuring some stuff so that he can use it as a regular user and not admin. I began downloading cool Ubuntu wallpapers for his amusement and I saved it in HIS "pictures" folder.

I want to be able to look at his pictures folder (from my login, which is admin) and copy the wallpapers to other users "picture" folders so that they may have them as well...

how to do this?

---

### Post by taurus on 2009-04-12
You just change permissions with his account so you can access his.  Assuming his username is brother, do

```
sudo chmod -R 755 /home/brother
ls -la /home/brother/pictures (or /home/brother/Pictures since Unix/Linux is case sensitive.)
```

---

### Post by ayastona on 2009-04-12
taurus, thanks for your help but i am having a bit of a problem.

here is what happens after the first command (sudo chmod -R 755 /home/brother)

[sudo] password for brother: 
brother is not in the sudoers file.  This incident will be reported.

what do i do next?

---

### Post by _Purple_ on 2009-04-12
> **ayastona said:**
> I have set up a new user for my brother so he can use my computer and learn linux!

I set up his account under his name and started configuring some stuff so that he can use it as a regular user and not admin. I began downloading cool Ubuntu wallpapers for his amusement and I saved it in HIS "pictures" folder.

I want to be able to look at his pictures folder (from my login, which is admin) and copy the wallpapers to other users "picture" folders so that they may have them as well...

how to do this?

You can open the GUI as admin by typing it in terminal:
```
gksu nautilus
``` 

Then copy the picture files from /home/brother's_username/pictures and place them in any user's picture folder /home/any_username/pictures.

---

### Post by codeseer on 2009-04-12
If you're on his account, you can just go and right-click the Pictures folder and change the permissions.

---

### Post by ayastona on 2009-04-12
_Purple_

See originally i thought it would be as simple as to just use the GUI and copy, paste, drag, whatever i needed into the other user folders....

turns out that when i go to the lowest level directory (meaning the folder "/" with  folders bin, boot, dev, usr, lost+found, lib, opt, etc, etc, etc... i cant find the "brother" folder anywhere!

maybe im looking in the wrong place?

---

### Post by codeseer on 2009-04-12
> **ayastona said:**
> _Purple_

See originally i thought it would be as simple as to just use the GUI and copy, paste, drag, whatever i needed into the other user folders....

turns out that when i go to the lowest level directory (meaning the folder "/" with  folders bin, boot, dev, usr, lost+found, lib, opt, etc, etc, etc... i cant find the "brother" folder anywhere!

maybe im looking in the wrong place?

I tested it in VirtualBox and was able to view the home folders of both a 'desktop user' account and a 'unprivilaged' account under an 'admin' account.

'brother' will be under /home.

Edit:

I was able to view the pictures under the Pictures folder (/home/brother/Pictures) as well, without setting up any special permissions.

I logged into the 'brother' account and right-clicked the Pictures folder, clicked Properties, went to the Permissions tab, under Others at the bottom I changed 'Folder access' to 'Create and delete files' and 'File access' to 'Read and write' by clicking the drop-down menus. I was then able to drag/drop pictures into 'brother's Picture folder.

---

### Post by taurus on 2009-04-12
Is _brother_ his actual username?  I was using brother as an example so you need to replace it with the actual login name of that account.

```
ls -la /home
```

---

### Post by Iowan on 2009-04-12
Are you logged in on his account - or yours? You may be able to do the same (similar) thing from your account - since your username is in the admin group. Presumably... (hopefully?) your brother is not in that group.  He could be added, if you trust him...

---

