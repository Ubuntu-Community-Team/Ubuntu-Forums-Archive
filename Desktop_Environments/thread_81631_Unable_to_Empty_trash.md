---
title: "Unable to Empty trash"
date: 2005-10-24
forum: Desktop Environments
---

### Post by sammyguy193 on 2005-10-24
When I try to delete anything this is what I get:


-------
Could not write to file /home/dragoon/.local/share/Trash/info/trash.trashinfo.

-------


suggestions?

thanks,
sam

---

### Post by cwaldbieser on 2005-10-24
[QUOTE=sammyguy193]When I try to delete anything this is what I get:


-------
Could not write to file /home/dragoon/.local/share/Trash/info/trash.trashinfo.

-------


suggestions?

thanks,
sam[/QUOTE]
Did you check the permissions on that file?  Maybe they got set to read-only somehow?

---

### Post by sammyguy193 on 2005-10-24
no, permissions arent an issue. I would assume I have R/W access to everything in my home dir, I simply cant delete anything. both moving the icon to the trash and selecting the file and hitting the delete key dont work, and I havent tried command line because if i have to use that from now on, i'll just do a clean install..... which I dont feel like doing... 


thanks
sam

---

### Post by Staesys on 2005-10-24
I'm not saying this is the answer, but when it comes to computers, I've learned one simple rule when dealing with them:

**Don't assume anything.**

I personally have had instances where some files and folders somehow became the property of root and I no longer had permission to do anything with them.

**Update:**

I just went in as root and changed my permissions so that root was the owner and noone else could write or modify the info folder and it's contents. This is the error I got:

[B]Could not write to
file /home/paul/.local/share/Trash/info/amarok-1.3.3.tar.bz2.trashinfo.[/B]

---

### Post by blastus on 2005-10-24
[QUOTE=Staesys]I personally have had instances where some files and folders somehow became the property of root and I no longer had permission to do anything with them.[/QUOTE]

I can verify this has happened to me too. I just reinstalled Kubuntu and kwrite worked for a little while but then started going wonky complaining that ~/.kde/share/config/kwriterc was not writable. So I had to chown it yet again because it somehow got chowned by root.

---

