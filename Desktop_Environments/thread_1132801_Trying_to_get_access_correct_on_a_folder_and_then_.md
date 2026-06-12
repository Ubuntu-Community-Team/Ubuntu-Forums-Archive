---
title: "Trying to get access correct on a folder and then share it with SAMBA"
date: 2009-04-22
forum: Desktop Environments
---

### Post by zenobiaflex on 2009-04-22
I am trying to utilize some drive space I have in my old PC with Ubuntu 8.10 to offload some stuff from one of the USB drives that is connected to my time capsule. I emptied a 200Gb hard drive in the computer and formatted it as Ext3. I then set a mount point so I could access it and then also set it up to share. I followed directions for here:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)


I set the permissions so that a group I had called sambashare could access it. Now I have the following problems:

When trying to copy from the USB drive that is attached to the TC, it will let me drag and drop or copy paste files, but not folders. It will give me a file or folder not found error and then a little icon that looks like a piece of paper with the name of the folder will appear on the new hard drive. If I manually create a folder and then drop just files into it, that is no problem.

Also, when I go to my macbook, I try to connect to the share using the ip address (smb:\\192.168.X.X)... it will show me the folder in a list, when I select it, it asks for the username and password. If I give the username and password for my user on the Ubuntu computer, it isn't able to connect.

The only thing I haven't tried is going back to that website above and using the exact permissions that are given there... assigning the "plugdev" group with the permissions to see if that makes it all work.

Any ideas?

---

