---
title: "samba alt install"
date: 2009-04-28
forum: General Help
---

### Post by 762sks on 2009-04-28
i downloaded samba with swat and want to install it. i downloaded the latest in a tar.gz files format. i unzipped it to the desktop, and now im not sure where to go from here. 

i know that there is already a tutorial on installing samba, tried it and not having much luck with it. i thought maybe this way with the graphocal interface it might help. 

i know in xp  you usually just double click the .exe file to install stuff, but what about link what does it use? do i have to run a terminal command? 


thanks 

762sks

---

### Post by cariboo on 2009-04-28
It would be much better if you installed samba from the repositories, swat is also in the repositories.

Personally I don't like using swap as you have to run it as root in order to edit /etc/samba/smb.conf.

Have a look at this [thread=202605]howto[/thread]

---

### Post by cookie132 on 2009-04-28
Install via apt-get in the command line:
sudo apt-get install swat
sudo apt-get install samba

---

### Post by 762sks on 2009-04-28
ok thanks guy i didnt know that.

---

