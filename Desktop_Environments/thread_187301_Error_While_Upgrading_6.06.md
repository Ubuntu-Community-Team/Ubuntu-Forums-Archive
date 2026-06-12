---
title: "Error While Upgrading 6.06"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Magiczero on 2006-06-02
Hello

I ran system updates and tried to download the new 6.0.6 and here are the errors I got

Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found
 
What do these errors mean?  How can I fix them?  
Thanks

---

### Post by johnc4510 on 2006-06-02
These are repositories that I believe automatix installed and that you no longer need. To remove these do this:
Applications>Accessories>Terminal
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
In the window that opens, put a # in front on those three lines, or take them out completely. Save the file and close the window.
sudo apt-get update
sudo apt-get dist-upgrade
This will upgrade you to dapper 6.06

---

### Post by Magiczero on 2006-06-02
I get the error
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
when trying to upgrade.  fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

What does this mean?  **_I need help!_**

---

### Post by johnc4510 on 2006-06-02
Did you follow the instructions I gave you above?

---

### Post by Magiczero on 2006-06-02
yes and it wont work!!  Can I just unistall automatix?

---

### Post by cjazz on 2006-06-02
No offense, seriously, but if I were you I would go back and follow johnc4510's instructions above ... carefully, one by one. If you're still getting error messages referring to the problematic repositories you've mentioned, I can only think of two problems: Either your /etc/apt/sources.list file still has those lines or you failed to do

sudo apt-get update

before doing sudo apt-get dist-upgrade. Apologies if I'm wrong.

---

