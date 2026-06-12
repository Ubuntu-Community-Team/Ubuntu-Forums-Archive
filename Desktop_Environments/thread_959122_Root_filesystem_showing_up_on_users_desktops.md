---
title: "Root filesystem showing up on users desktops"
date: 2008-10-26
forum: Desktop Environments
---

### Post by bennetfox on 2008-10-26
Hey gang!

I've got Kubuntu 8.04.1 installed on another machine and when I create user accounts on that machine, there are folders on the desktop that display the root filesystem, i.e. /bin, /boot, /lib, etc. These folders cannot be deleted by the users and they are not showing up in the users home directory. Any ideas on what's causing this and how to fix/delete these folders and keep it from happening again when new accounts are created?

---

### Post by ronnielsen1 on 2008-10-26
That's weird. Are they links to the actual /bin /etc ? or are they empty folders? If you go to konqueror and migrate to /home/username/Desktop - do they show up?

---

### Post by bennetfox on 2008-10-26
They're not links, they're the actual directories themselves. You can click on them and you can see all the files inside. As I said, the users can't delete them and I really don't want to try to delete them as root because I don't want to delete the entire filesystem and have to do a reinstall.

What do you mean by <i>migrate</i>?

---

### Post by ronnielsen1 on 2008-10-26
I just meant for you to go to /home/username/Desktop in konqueror and see if the icons are in there and if they're actual files or links.

---

### Post by bennetfox on 2008-10-26
Ah, Gotcha.

I got it to working correctly. You see, I've installed FreeNX and have been using the nomachine client to connect to the box and create user accounts. I looked through the user's home directories and saw that there was no Desktop directory and none of the other directories that Ubuntu creates in that directory. To fix it, I had to log into the machine locally using each user's name and password so Ubuntu would create the proper directory structure. All of the root filesystem folders are gone and now they're getting the normal desktops.

I find it weird that when a user account is created the process should automatically create the necessary directory structure for the /home/username directory without having to log into the machine locally. Hopefully there will be some fix for this in the future.

Thanks for your help!

---

