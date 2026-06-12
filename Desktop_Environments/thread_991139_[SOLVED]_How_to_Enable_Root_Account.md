---
title: "[SOLVED] How to Enable Root Account?"
date: 2008-11-23
forum: Desktop Environments
---

### Post by smccarthy945 on 2008-11-23
I need to know how to enable the root account? I tried sudo passwd command and I still cannot login as root from the GUI. It says System Administrator account not allowed to login from this screen??

The reason I need to enable the account is the fact that when I go into COMPUTER and try to create folders, my current account doesn't have access through the GUI. Is there any way to run the COMPUTER icon with the SUDO command?

---

### Post by unix192 on 2008-11-23
Firstly you should set the root password. Login to ubuntu with the user which you created during installation. Go to System> Administration> Users and Groups. Select root. Click on Properties. Set the root password.
 Secondly enable the root login. Click on System> Administration> Login Window. Click on Security tab. Check “Allow local administrator login“. Click on OK.
 Everything is done. Now logout and log in with your root account.
A Word of CAUTION: Use your root account only when absolutely necessary. Never user root account for daily works. For regular work use the account created at installation time.
 Reason: Root is the superuser. It has got all the unrestricted privileges to perform any tasks. Its like “I can do anything“.
 While running as normal user you would be prompted for your password when you try to make a major change to system settings. Thus you would be alerted that your step is making some changes if you are ignorant of the step you are taking.
 A virus is a program or script that intends to harm your system by changing the settings or configuration. At that stage you would be prompted for password, thus you can get warned.

---

### Post by eldragon on 2008-11-23
explain what going to my computer and creating folders means...


you should be able to create folders within your home only.

that should be enough for every day work.

example. my home is located at
```

/home/eldragon/

```

i can only write inside that folder (and any subfolder within it).

---

### Post by aysiu on 2008-11-23
Read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

It will help you create system folders, which appears to be what you want to do. Normally, you should be able to create any folders you want under /home/*username*/ (non-system folders).

---

### Post by smccarthy945 on 2008-11-23
YESS!!! This is what I was looking for. GKSUDO and then the program to run in sudo. I didn't know how to ask it but the GKSUDO command is what I was looking for. Thanks!!

---

### Post by Swagman on 2008-11-23
I thought it was sudo su ?

---

