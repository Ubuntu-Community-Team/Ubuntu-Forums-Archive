---
title: "How do I print from Ubuntu to a printer connected to an XP computer on my network?"
date: 2008-12-05
forum: General Help
---

### Post by andrewwg94 on 2008-12-05
I'm trying to print to a printer connected to a windows xp computer. i've enabled unix printing in xp.

ip address of computer: 192.168.15.103
share name: Laser1320

please, any help greatly appreciated.

---

### Post by spcwingo on 2008-12-06
Try installing samba and smbfs.  Then use the printer configuration under system>admin>printing>new printer>windows printer via samba.  Then just follow the on screen instructions.;)  Let me know if that get her going.

---

### Post by plucky on 2008-12-06
Also this [link](https://help.ubuntu.com/community/WindowsXPPrinter) might help.


Good Luck

---

### Post by stinger30au on 2008-12-06
no need to install unix printing on the windows box

install the printer in say xp and then once it is up and running you need to share it


start , printers, then click the printer and right click share and call it say "printer"

you should be able to in the ubuntu box , so long as it is on the same lane, just to make life easy

then hit system , adminsitration printing on the ubuntu box

click new

wait for it to finish searching
click windows printer via samba
click browse
search for the pc and click the printer

you may need to install a generic driver. for example, to print to a new hp laser printer you may need to install hp laser jet 6 drivers on your ubuntu pc to print to it as there aint the latest and greatest drivers there in the cups data base

if the windows pc needs a user/password make sure you type this in also on the printer setup scren and make sure you hit the 

set authentication details and test it
if it fails right here, dont go any further, your wasting your time

make sure the user name and passwords are right. once they are correct, the ubuntu pc will even tell you when you got the user name passwords correct as it will test it, then move forward and it will create a printer icon for you to print to thr windows box

---

### Post by bayvista on 2008-12-13
Many thanks for this. I neglected to add the username/password at first and it just sat there. When I reread your article, I went back and added the username/password and bingo! It all worked like magic.

---

