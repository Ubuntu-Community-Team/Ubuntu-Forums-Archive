---
title: "Unable to delete folders in the trash bin"
date: 2014-04-21
forum: Desktop Environments
---

### Post by priscilla2 on 2014-04-21
Hello,
I'm trying to empty my trash bin without success. I can delete easily some files and folders, but others cannot be deleted at all. I've tried to delete them through the terminal with these codes below, but without success.
sudo rm -rf /home/username/.local/share/Trash/*

sudo rm ~/.local/share/Trash/files/*

Does anyone know how to forcibly delete those folders? 

btw, those folders are 'simple' folders, if I'm not mistaken, none of those can offer any risk if deleted.
Thanks in advance!

---

### Post by monkeybrain20122 on 2014-04-21
Try without sudo. This may not be the reason why you can't delete, but in general you don't need sudo to change things in your home (unless you moved something there as root). There are quite a bit of abuse of sudo which is not good for security. The whole idea of using sudo instead of logging in as root is to invoke root privilege only when necessary, some people who write online tutorials seem to think that you need sudo for the terminal.

In the future you may want to actually delete instead of sending things to trash (it is the most stupid design IMO. probably "inspired" by Windows) Open Nautilus (aka Files) then in Files > Preferences > Behaviours check the box include an option to delete bypassing trash, this will show up when you right click to delete something next time, just delete instead of moving it to a  folder to take up space.

---

### Post by priscilla2 on 2014-04-21
I've tried without sudo and it didn't work at all. It doesn't return me any error. I run the code, but it stays running forever and the folders are still there.
I've  tried "sudo nautilus" to access the trash, but it doesn't work either..  and then it returns me an error "This location could not be displayed.  Sorry, could not display all the contents of "trash:///": Operation not  supported"&#65279;

---

### Post by batden on 2014-04-22
Install Midnight Commander and run sudo mc ~/.local/share/Trash/files. Then press F8 to delete a folder.

---

