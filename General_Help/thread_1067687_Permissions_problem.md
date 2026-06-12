---
title: "Permissions problem"
date: 2009-02-12
forum: General Help
---

### Post by arigwapo on 2009-02-12
I recently copied over some stuff to my server running Ubuntu 8.10.  Most had no problems whatsoever but there are certain files/folders that have a "lock" emblem on them and when I check on permissions, they show owner as "nobody" and group as "nogroup" and won't let me move/delete them.  In Users and Groups there's just me and root (btw, can I delete root?)

How do I change permissions so I can move/delete the files/folders??

---

### Post by spiderbatdad on 2009-02-12
You can open your file browser as root with the command ```
gksu nautilus
```You have to be very careful in this mode. You can easily break your system if you start deleteing or moving files you have questions about; that is, unless you know what the file is, and why it's there, you probably shoudln't touch it. 

From your terminal you can also delete, move, and change file permissions. Use sudo in front of your commands, or sudo -i to get a temporary root shell...then run commands without the word sudo.

To change ownership:```
sudo chown -R newowner:newgroup somefolder
```
So if I were in the folder /var/www and I wanted to change the owner of the folder mp3 and all the songs in the folder from root to nobody I do: ```
sudo chown -R  nobody:nobody mp3
```If I were not specifically in the folder i give a complete path /var/www/mp3. If I only want to change a file, I do not need -R.

---

### Post by arigwapo on 2009-02-12
Great!!  That was easy!!!

---

