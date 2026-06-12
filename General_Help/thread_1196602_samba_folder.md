---
title: "samba folder"
date: 2009-06-25
forum: General Help
---

### Post by zeker446 on 2009-06-25
I there, i have a samba share with pdc, and i am building some kind of production software in php, but i have to upload orders to my samba share but it wont do, why? because my aplication creates a folder with the number of the orther and them it wont place any files inside it because de folder is created with only acess permition to other users, i have tested lots of option without any sucess cant you help me?


my samba share config:

[Y]
     comment = y
     path = ...
    read only = no
    create mask = 0777
    directory mask = 0777
    force create mode = 0777
    guest ok = yes
    writeable = yes

---

### Post by Divider on 2009-06-25
this isn't the most secure option, but its the best i can come up with, 

chmod -r your directory manually then setup .htaccess to keep snoopers out.

The .htaccess is pretty much your only protection at that point.

When your php script makes the folder it should have no problem. thats what i did to get a php upload script for photos to work. there is a better option then 777 though, it gives only the localmachine access, so when you use the scipt it thinks its happening on the machine.

Good luck.

Also make sure you make the samba share automount if its a seperate disk.

---

### Post by zeker446 on 2009-06-25
it didnt work same problem

---

### Post by Divider on 2009-06-25
you made sure you did -r?

ok step 2.

```
sudo chown "you" "directory" 
```

---

### Post by zeker446 on 2009-06-25
the problem is that php aplication creates de folders in the group others, so when it creates a folder that folder becames only with acess right to others user and it cant create subfolder inside that to upload pictures

---

### Post by snek on 2009-06-25
I had the same problem at work, I mad the folder public, writable for everyone and forcing it to one user:

under **[global]** i added:
```

guest account = nobody
map to guest = bad user

```
and then in **[share-name]** i have:
```

        path = /media/storage/dump
        browseable = yes   
        read only = no
        writeable = yes
        guest ok = yes
        guest only = yes
        force user = nobody     
        create mode = 777
        directory mode =755

```

Mind you this is on Debian Lenny but it should work the same under Ubuntu.
Of course you have to realise the security issues, but that's not the point of this thread :)

---

