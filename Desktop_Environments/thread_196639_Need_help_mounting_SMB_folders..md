---
title: "Need help mounting SMB folders."
date: 2006-06-14
forum: Desktop Environments
---

### Post by alejandrops on 2006-06-14
Hey, first time writing here :)
I'm having trouble trying to mount a SMB folder in a windows 2000.
the folder in question has permissions, so when I just browse in nautilus and try to get inside my foldes ir says that I dont have permissions (in spanish the message is: no tiene permisos suficientes para ver la carpeta).
I couldnt find a way for gnome to ask me the user and password, is there a graphical way to handle it? 
so I edited fstab and added: 
//198.0.0.200/misdoc/alejandro /media/Alejandro smbfs rw,defaults,username=aaaaaa%bbbbb       0      0

it didn mount ok, so I had to remove the last part of the path

//198.0.0.200/misdoc /media/Alejandro smbfs rw,defaults,username=aaaaaa%bbbbb       0      0

OK, now is mounted (Ubuntu needs an easy fstab editor!!!!, how can I help?)
but the problem is tha the folder ir read only, I cannot copy anything inside. If I open a file I can modifie it, but is impossible to create or copy a file.
I already tried  
chmod 777 /media/Alejandro
but nothing.

a clue?

thanks!

PS: In Kde is easier?

---

### Post by mjm115 on 2006-06-14
In KDE, you can use the smb4K app to easily mount shares.  I'm not sure if there is a program that exists like that for Gnome.

---

### Post by tronica on 2006-06-14
maybe you should start over

cd /mnt

sudo mkdir win

sudo chmod 777 win

sudo mount -t cifs //198.0.0.20/misdoc /mnt/win -o user=username,pass=password

---

