---
title: "Regarding the wine in Ubuntu 10.10"
date: 2011-01-12
forum: Desktop Environments
---

### Post by slkamath on 2011-01-12
Hello,

I am using ubuntu 10.10, I installed wine in this and i tried to install windows application i.e. Total Commander and it's installed too. but I cant able to find where it has got installed. If i go to wine it's shows "wine configure" window. So Please guide me how to find out the installed programs in wine.

Thanks in advance.

Regards

Lokesh Kamath

---

### Post by ankspo71 on 2011-01-12
Hi,
It is located inside a hidden directory called '.wine' inside your home directory. When you open your home folder using the nautilus file browser, you can press Ctrl+H to reveal hidden directories.

/home/yourname/.wine/drive_c/totalcmd 
(the default install location for total commander)
OR
/home/yourname/.wine/drive_c/Program Files/totalcmd 
(the typical location for windows applications)

Hope this helps

---

### Post by ankspo71 on 2011-01-12
Also, it should have created a start menu entry for you. I think it's located at: Application Menu > Wine > Programs > Total Commander. I'm not sure of the exact location because I'm not using a Gnome desktop. You might need to log out and back in again before it will appear in the menu too.

---

