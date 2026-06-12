---
title: "need help with my 2 AMD Radeon HD 6990"
date: 2011-11-09
forum: Desktop Environments
---

### Post by nokia2mon2 on 2011-11-09
hi there im new in ubuntu and really need a help.

i followed this guide
 [http://sites.google.com/site/nozyczek/home/wardriving/how-to-install-pyrit-with-ati-cal-support-under-backtrack-5-r1-gnome-64bit](http://sites.google.com/site/nozyczek/home/wardriving/how-to-install-pyrit-with-ati-cal-support-under-backtrack-5-r1-gnome-64bit)
 and every thing was smooth and i can see this in pyrit list_cores 
--------------------------- 
Pyrit 0.4.1-dev (svn [r308]("http://code.google.com/p/pyrit/source/detail?r=308")) (C) 2008-2011 Lukas Lueg [http://pyrit.googlecode.com]("http://pyrit.googlecode.com/") This code is distributed under the GNU General Public License v3+  The following cores seem available... #1:  'CAL++ Device #1 'AMD CAYMAN'' #2:  'CPU-Core (SSE2/AES)' #3:  'CPU-Core (SSE2/AES)' #4:  'CPU-Core (SSE2/AES)' #5:  'CPU-Core (SSE2/AES)' #6:  'CPU-Core (SSE2/AES)' #7:  'CPU-Core (SSE2/AES)' #8:  'CPU-Core (SSE2/AES)'
 --------------------------------
 after that i try to see my second radeon so i followed this guide (last comment):
 [http://code.google.com/p/pyrit/issues/detail?id=137#makechanges](http://code.google.com/p/pyrit/issues/detail?id=137#makechanges)   every thing is cool, and the second radeon show on, but after reboot the desktop items not shown and i cant click any thing in places, and i can see only one radeon
 --------------- 
  its 48 hours without sleeping trying to make the 2 GPU`S  work without problem.   i have only 1 screen.. samsung led  help me please ,, i think the problem is that the system guess i have multi Monitor.. really dkn
------------ 
by the way when i try replace in the 
/etc/X11/xorg.conf

with this line 
after reboot desktop came blank and i can see the terminal and can browse so i delete it
"aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0 Regards

---

