---
title: "Can't change regional and time date format on 9.10"
date: 2009-11-30
forum: Desktop Environments
---

### Post by j3fk4 on 2009-11-30
Hi,
I have just installed the Ubuntu 9.10 on office's computer. And the computer actually needs to be able to run the tax reporting program made by government which can only be run using windows.

So I go installed WINE, ran the tax reporting program installation, walla, done. The program is ready to use...........or not!
The program actually require me to change the regional to my country's regional and want the date on the top right corner to be changed from November 30,2009 into dd/MM/yyyy format

I searched and searched everywhere, even tried to edit the LCTIME etc craps, and then tried changing line 50 of USPtime.py in USR/LIB/PYTHON2.4 (but I dont even see USPtime.py in that folder anyway!), none helps.

So, please help!

Thanks

---

### Post by j3fk4 on 2009-12-03
**SOLVED**

Well it turns out to be easy,
after u install the wine, install the program that require you to have dd/MM/yyyy format.
after that, change the registry of the wine at HKEY_CURRENT_USER\ControlPanel\International\sShortDate to dd/MM/yyyy

remember that u need winetricks and cabextract in order for this to work
go to sudo regedit to change the registry.

don't need to change the ubuntu time format at all.

---

