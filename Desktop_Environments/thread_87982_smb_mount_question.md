---
title: "smb mount question"
date: 2005-11-09
forum: Desktop Environments
---

### Post by vtec on 2005-11-09
I have a windows share that i need to have mounted. It requires a username and password. What is the best way to do this so that everyone on the system can read and write it. I have tryed to mount it right inside of gnome but then it is always asking me for my password for all the shares on the server. I only have access to one so i have to hit cancle for each share that i have no access to. I then mounted it by placing it in the fstab. However only root can wirte to it now. Is there an easier way of doing this???

---

### Post by HermanAB on 2005-11-09
Your fstab method is the right one.

Add ',user' in the fstab options string to allow users to mount. (Look at the cdrom mount string for help).

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by Joe_lurker on 2005-11-09
There is a HowTo:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I haven't tried it but it looks like it is what you want.

-Joe

---

### Post by vtec on 2005-11-09
I tryed adding user, but that didnt seem to work. (user does work for my nfs drives) From the linked howto i kinda got it working. I had to add my user id which allows me to wirte to it, but i don't think any other user will be able to. Thanks for the help though. It works good enough for the time being.

---

