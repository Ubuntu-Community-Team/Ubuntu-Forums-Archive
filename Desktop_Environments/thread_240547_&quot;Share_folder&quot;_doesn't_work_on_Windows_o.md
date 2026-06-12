---
title: "&quot;Share folder&quot; doesn't work on Windows or Mac"
date: 2006-08-21
forum: Desktop Environments
---

### Post by rsk on 2006-08-21
Using Dapper Drake (6.06) and right clicking on a folder and selecting "Share", then selecting (the first time) to add Samba and NSF support, then sharing the folder under a given name and hitting OK results in me not being able to see that folder from Windows XP Pro or my MacBook Pro (Mac 10.4.6)

Each time I've needed to share a folder, I've found the link to UbuntuGuide:
[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

and I end up fighting with Samba config files for an hour before my Mac can see the folder, but still can't get Windows to see it.

What I really want to get done is exactly what the GUI suggests I can do, and that is to right click on a folder, share it, and be done with the whole ordeal (see it on Windows and Mac).

Am I missing why this is so complicated? Maybe there is some fundamental misunderstanding I'm having that makes me think I can do the share in this fashion and infact it's not the right way. Just looking for a nice and easy point and click experience like under Windows or Mac, thanks for any pointers.

---

### Post by rsk on 2006-08-21
The way this guide explains the process is exactly how I expected it to work:
[http://www.linuxquestions.org/linux/answers/Networking/File_sharing_with_OS_X_using_Ubuntu_5_04](http://www.linuxquestions.org/linux/answers/Networking/File_sharing_with_OS_X_using_Ubuntu_5_04)

But it never does (I've tried twice with two different installs). My Mac never sees the Samba share or even the server until I end up fiddling with the Samba config files like I mentioned using the UbuntuGuide as the guide.

Is there some sort of timeout/refresh issue here? For example, if  share a folder, should I give it alteast 5mins before I see it popup on my network?

Also my network config is fine, everybody is all behind the same router, and as I mentioned, after about an hour of messing with my Samba config files, I got it working (with no adjustments to my router), but I really want a point and click experience, no config files please.

---

### Post by rsk on 2006-08-21
I also had this problem (being asked for authentication that never works, always fails):
[http://www.linuxforums.org/forum/linux-networking/55632-cannot-logon-share-folder.html](http://www.linuxforums.org/forum/linux-networking/55632-cannot-logon-share-folder.html)

Which seemed to only get fixed when I went through the tips in UbuntuGuide when adding the user to the SMB user list and generating a password for them and everything (again more not-pointing-and-clicking-experience)

Is this a limitation I'm not aware of or a requirement if I want a name/password? (can't do it from the interface)

---

