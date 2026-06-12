---
title: "super user"
date: 2008-04-20
forum: Desktop Environments
---

### Post by dch55 on 2008-04-20
In the new Ubuntu 8.04 I went and set the root password as I have done in previous versions, that way I can run programs as super user If I want.  For whatever reason this release deletes the /home/root directory which will not allow you to install any programs under add/remove or the synaptic package manager.  In order to be able to install programs again you need to run the following commands
1.open terminal
2.move to the home folder
3.type 'sudo mkdir root'
4.this will create the directory and allow you to install again

hopefully if any one runs into the same problem i did this will help.
If there are any other ways around this please post them.

---

### Post by GeigerRulesBig on 2008-04-20
It is hazardous to always run as the super user, that is why the root directory is limited. Instead of logging in as root you can use ```
 SUDO (command) 
``` to execute commands in the terminal with root privileges. It is better to stay logged in as a normal user and only elevate your power temporarily to super user when you need to.


-Geiger

---

### Post by kellemes on 2008-04-21
> **dch55 said:**
> In the new Ubuntu 8.04 I went and set the root password as I have done in previous versions, that way I can run programs as super user If I want.  For whatever reason this release deletes the /home/root directory which will not allow you to install any programs under add/remove or the synaptic package manager.  In order to be able to install programs again you need to run the following commands
1.open terminal
2.move to the home folder
3.type 'sudo mkdir root'
4.this will create the directory and allow you to install again

hopefully if any one runs into the same problem i did this will help.
If there are any other ways around this please post them.

Don't tell me you've read the documentation ;-)
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

You should read up on sudo, you can do all kind of cool stuff with it.
[http://www.wlug.org.nz/SudoHowto]("http://www.wlug.org.nz/SudoHowto")

---

### Post by dch55 on 2008-04-22
Thanks for the links.  I know of the sudo command but have just always preferred su then exiting when I am finished.  But i do need to be more security conscious.  Thanks

---

