---
title: "edit the /usr folder"
date: 2009-03-23
forum: General Help
---

### Post by sansa dude on 2009-03-23
i am trying to add plugins to amsn but for me to access it i need root rights, how do i do this so i can edit this folder and is there a way to change the permissions permanently so i can edit that file on a regular basis?

---

### Post by aeiah on 2009-03-23
changing the rights could cause all sorts of problems. its really not worth giving yourself permanent root permissions. i think there are some nautilus scripts to do things like 'open root nautilus here' etc

anyway, the best thing to do would be to temporarily grant the program nautilus root permissions. open a terminal and do:

gksudo nautilus

---

### Post by sansa dude on 2009-03-23
ok is there a way i can change the permissons on the amsn file alone? when i go to properties. permissions it say it is owned by root

---

### Post by rockstone on 2009-03-23
If you want to change the owner you could use sudo chown USERNAME PATH, or you could change the permissions by using sudo chmod 666 PATH. It is probably best to just change what you need by using gksudo nautilus though. I am not sure what problems might occur if you change the owner/permissions.

---

### Post by SuperSonic4 on 2009-03-23
You can also copy them to ~/.amsn/plugins

this has the advantage of being able to be done as user but cannot be used by anyone else on the system.

It'd be better to give nautilus root permissions for what you need to do although you can use the terminal to move the folder. In a terminal:```
sudo mv -fv ~/Desktop/<folder_name> /usr/share/amsn/plugins/
``` or ```
mv -fv ~/Desktop/<folder_name> ~/amsn/plugins/
```

---

### Post by sansa dude on 2009-03-23
SOLVED i found a link of google that explained it i edited only the amsn file

---

