---
title: "Instlling Nessus"
date: 2008-12-30
forum: General Help
---

### Post by Mechina on 2008-12-30
Hey guys I'm trying to install Nessus on Ubuntu 8.10. I followed this guide: [http://ubuntuforums.org/showthread.php?t=27674](http://ubuntuforums.org/showthread.php?t=27674) but there a problem, when I type:

```
sudo nessus-adduser
```

it doesn't work. I enter my desired login and then pass but it just keeps going asking me for a pass over and over, like this:

```

niki@niki-desktop:~$ sudo nessus-adduser
[sudo] password for niki: 
Using /var/tmp as a temporary file holder

Add a new nessusd user
----------------------


Login : root
Authentication (pass/cert) [pass] : root
Authentication (pass/cert) [pass] : root
Authentication (pass/cert) [pass] : root
Authentication (pass/cert) [pass] : root 
Authentication (pass/cert) [pass] : root
Authentication (pass/cert) [pass] : root
Authentication (pass/cert) [pass] : root
Authentication (pass/cert) [pass] : root
Authentication (pass/cert) [pass] : root

```

Anyone have an idea on how to fix this? Thanks.

---

### Post by garymc1 on 2008-12-30
use this to install,

sudo apt-get install nessus
sudo apt-get install nessusd
sudo nessus-adduser
sudo ln -fs /etc/init.d/nessusd /etc/rc2.d/S20nessusd
sudo /etc/init.d/nessusd start
sudo gedit /usr/share/applications/Nessus.desktop

Insert the following lines into the new file

[Desktop Entry]
Name=Nessus
Comment=Nessus
Exec=nessus
Icon=/usr/share/pixmaps/nessus.xpm
Terminal=false
Type=Application
Categories=Application;System;

After that you can find Nessus in the Gnome menu under Applications -> System Tools.

when it promps,, Authentication (pass/cert) [pass] :

just press return then you enter your password

thanks

Gary

---

### Post by Mechina on 2008-12-30
thanks a bunch man, all i had to do is press enter haha

---

### Post by garymc1 on 2008-12-30
No problem, 

Please mark this thread as solved

Cheers

Gary

---

