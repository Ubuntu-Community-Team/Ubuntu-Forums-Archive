---
title: "Install Ubutu studio theme on ubuntu"
date: 2007-05-11
forum: Desktop Environments
---

### Post by yinglcs2 on 2007-05-11
Hi,

Can you pleaes tell me if it is possible to install ubuntu studio theme (the black/blue theme) on my ubuntu?

[http://ubuntustudio.org](http://ubuntustudio.org)

if yes, please tell me how?

Thank you.

---

### Post by hju on 2007-05-11
From [http://ubuntuforums.org/showthread.php?p=2632620#post2632620](http://ubuntuforums.org/showthread.php?p=2632620#post2632620)

> **greenpete said:**
> I'm running it now!
If you gou go to the download page you will see the terminal commands to run...
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

and

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

then run..
sudo apt-get install ubuntustudio-theme

Hope this helps, it worked for me!

Peter

P.S. Then change your theme in the normal way!

---

### Post by noctis_vulpes on 2007-11-09
Um... I'm trying to install Ubuntu Studio theme on Feisty... Every singly googled information is essentially the same as this post:

[http://ubuntuforums.org/showpost.php...&postcount=190](http://ubuntuforums.org/showpost.php...&postcount=190)

except that it's not working. There doesn't seem to be a host named archive.ubuntustudio.org, and I can't find any information as to what I need to change in order to get this theme installed. Any idea waht I need to do?

---

### Post by peacepipejv on 2007-11-11
Same problem here. Cant get the key. no valid OpenPGP data found. Im assuming it has to do with the 7.04 repo closing. Havent made the jump from Ubuntu feisty yet. Is a Ubuntu 7.10 upgrade required?

---

