---
title: "Cannot create &quot;root password&quot;"
date: 2004-10-18
forum: General Help
---

### Post by krillehb on 2004-10-18
Hi  :D 

it´s somehow impossible to create a root password.
I did it as written in the Ubuntu FAQ´s but my Ubuntu System ( 4.10 )
doesn´t create it.

What i shall do, i need to create one to make some changes on my system for which i need a root password ( for example setting/changing time zone etc. )

Can someone help me ?? ( In English or German )

Regards
Krille

---

### Post by adbak on 2004-10-18
I don't know for sure, but I believe it's ```
sudo passwd root
``` although I could be wrong.  You might even want to the try the root terminal.

---

### Post by kenchuamy@gmail.com on 2008-06-07
thanks, is so simple, u make my life easier.....

---

### Post by kenchuamy@gmail.com on 2008-06-07
dear sir, 
i successful create the root password, but "permission denied",what is that mean?
i just want to try to install joomla 1.5.3 into "/var/www", but permission denied when i using root password.

why and how come??

many thanks, newbie

---

### Post by sisco311 on 2008-06-07
You don't need to enable the root account.

Prepend "sudo" to all commands you would run as root.
When sudo asks for a password, it needs YOUR USER password, and not the root account password.

To run GUI applications as root use gksu. For example to run the file browser as root:
```
gksu nautilus
```
I recommend you to disable the root password
```
sudo passwd -l root
```For more information: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

