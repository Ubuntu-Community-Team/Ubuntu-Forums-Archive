---
title: "Menu bar disappeared after login"
date: 2013-12-18
forum: Desktop Environments
---

### Post by satimis on 2013-12-18
Hi all,

Ubuntu 12.04
Unity desktop

After login as satimis, the administrator, only background displayed with menu bar

If login as guest the menu-bar displayed.  On /home the folder /satimis is lost.

On terminal I can't
su satimis
su root

Operation is not permitted

How can I restore satimis login to display the menu bar? Thanks

remark:
Having tried reinstall "unity"

satimis

---

### Post by grahammechanical on 2013-12-19
I am a bit confused.

You should not be able to access the /satimis folder from a guest log in. In Ubuntu we do not use "su," we use "sudo." You may be running an incorrect command. When we open a terminal using Ctrl+Alt+T or through the Dash, we are logged in as our user. When we run commands that only the administrator can run (that would be us) we put sudo in front of the command and we are then asked for our password. After typing out our password the command will run. And we will continue as administrator for a few more minutes. Then we will revert to ordinary user.

May I suggest that you log in as yourself and when you get to a desktop you right click the desktop and select Change Desktop Background. That will open System Settings>Appearance. From there you can get to the front page of System Settings. From there select Additional Drivers. I suggest that you try another video driver.

Regards.

---

### Post by satimis on 2013-12-19
> **grahammechanical said:**
> I am a bit confused.

You should not be able to access the /satimis folder from a guest log in. In Ubuntu we do not use "su," we use "sudo." You may be running an incorrect command. When we open a terminal using Ctrl+Alt+T or through the Dash, we are logged in as our user. When we run commands that only the administrator can run (that would be us) we put sudo in front of the command and we are then asked for our password. After typing out our password the command will run. And we will continue as administrator for a few more minutes. Then we will revert to ordinary user.

May I suggest that you log in as yourself and when you get to a desktop you right click the desktop and select Change Desktop Background. That will open System Settings>Appearance. From there you can get to the front page of System Settings. From there select Additional Drivers. I suggest that you try another video driver.

Regards.
Hi,

Thanks for your advice.

$ su satimis
with satimis' password.  I can login its home

Your are right.  Each user has his own background avoiding confusion.


After copying all data to a spare HD preparing to wipe out the OS, I made a last check on user accounts to see whether there are data which I haven't copied.  I can't remember exactly how many users have been created in the past because this box was built >5 year ago.

On -> System Settings -> User Accounts
I found the user-satimis was locked.  After unlocking it the menu bars, top and side, come back.  I have rebooted the PC several times including shutdown making sure it works.

It is quite strange to me running update and upgrade will cause locking the administrator's account.

Rgds
satimis

---

