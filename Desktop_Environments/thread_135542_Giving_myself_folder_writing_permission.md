---
title: "Giving myself folder writing permission"
date: 2006-02-24
forum: Desktop Environments
---

### Post by cobbweb on 2006-02-24
Hi, 
 
   I have an apache sever installed on my computer and i would like to just save files into the "www" folder. My problem is that is say's i dont have permission and every time i wanna move a file in that folder i have to "sudo mv" the folder into the "www" file. I cant figure out how to make it so that i can just save right into that folder. Is there some config thing i need to do? Any help is wanted thank,s 

 Cobbweb

---

### Post by heimo on 2006-02-24
Add yourself to www-data group, change files and directories under /var/www/ to belong to www-data group and give it proper permissions.
```
adduser username www-data
``` 
Then use chmod and chown to change permissions for files under /var/www. If neccessary, see Kyrals [terminal for beginners]("http://www.ubuntuforums.org/showthread.php?t=73885") thread for instructions.

---

