---
title: "Login(GUI)  succeeds only with guest account"
date: 2013-02-20
forum: Desktop Environments
---

### Post by hms666 on 2013-02-20
Ubuntustudio [COLOR=Red]12.10 x64[/COLOR] with both [COLOR=Blue]XFCE[/COLOR] and [COLOR=Blue]Unity[/COLOR], wich both worked fine for "main" user before, but now when trying to login, it just shows black screen breefly and returns to logonscreen. The guest account goes fine to the desktop with both XFCE and Unity.

This started after AMD 13.2beta6 driver install, I did revert back to ubuntus fglrx (tried both open and closed) still same black flash and back to logon. Also tried reinstallin the beta6 driver.


I made a new user from guest account and that worked,  then in terminal #su <old user> and  added it to Admins with 
#sudo  usermod -aG sudo <newusername> , 
so what's broken from original user?

this is NEW users fglrxinfo
guest-w7povq@rry-NiX:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series 
OpenGL version string: 4.2.11903 Compatibility Profile Context


Solved ---> With the new temp account made copy of important stuff of home folder and then emptied, logged fine and copied back the old stuff.

---

