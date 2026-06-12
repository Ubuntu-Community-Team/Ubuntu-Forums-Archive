---
title: "Permissions Problem"
date: 2009-06-19
forum: General Help
---

### Post by lobo235 on 2009-06-19
I installed Ubuntu on an extra machine that I am using as a webserver. I created a proftpd account for my friend which allows him to upload to his home folder that I created for his user. He has an htdocs folder I created that he uploads web content to and I placed a symbolic link to his htdocs folder in my web root where I wanted it to show up. That's all working fine and he can upload files and see them on the webserver.

The problem I am having is that the files he is uploading are showing up with owner:group as friendsusername:users and I need them to show up as friendsusername:www-data so that the webserver can modify the files. He has installed wordpress and he is trying to edit some theme files.

Is there any way for me to make the owner:group sticky for the whole htdocs directory so that when anything is copied to it the right group will be applied to the files? Is this something I can just do with Ubuntu or is it something I need to tell proftpd to do when he uploads the files. I also need the files to have 775 permissions.

Any help is greatly appreciated!

---

### Post by clonne4crw on 2009-09-28
From within Nautilus, you can simply right-click the folder > properties > permissions. Does this work for you?

---

### Post by scouser73 on 2009-09-29
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by lobo235 on 2010-06-14
Is there a way to have this done automatically without me having to change the permissions every time he uploads the files?

---

