---
title: "launching Doom 3 under sudo"
date: 2005-10-30
forum: Gaming &amp; Leisure
---

### Post by PriceChild on 2005-10-30
Hey... i've got doom 3 working absolutely perfectly!

However, i'd like to create a launcher instead of typing "sudo doom3" into the terminal each time. It must be sudo'd in order to save and load savegames. However, a "sudo su -" followed by a "doom3" doesn't allow the opengl to load.

"gksudo doom3" doesn't seem to work as a launcher.

Please help, Pricey

---

### Post by ubuntumaneh on 2005-10-30
in .bashrc or .bash_aliases insert appropriately:

alias doom3='sudo doom3'

you still have to insert your password. But it is a beggining.

---

### Post by aneeshm on 2005-10-30
Are setuid scripts allowed ? Because that may work .

---

### Post by mo_x on 2005-10-30
Better find out why you need to use sudo. Probably some file permissions are not set correctly, check the ~/.doom3 directory.

---

### Post by PriceChild on 2005-10-30
all of the permissions in usr/local/games are set to root.

I can't figure out whether the save directory is here too though?

Im happy typing password each time though, it's just the strain of moving the mouse and clickign several times then typing out two commands :P

Thanks, Pricey

EDIT

where is .bash and .bash_aliases? :)

---

### Post by mo_x on 2005-10-30
The games are probably saved in the directory /home/<username>/.doom3. Because it start with a "." it is a hidden directory, you might have to set some option to see it.

---

### Post by frenkel on 2005-10-30
Don't ever run games like that as sudo. That's a very Bad Thing. It's like in windows, when everybody is administrator. Try to start it as a normal user and tell us what error messages you get.

---

### Post by PriceChild on 2005-10-30
The game works fine as a normal user! however it just won't save, or load savegame files.

EDIT

Ok, i've found the save game files :D

However, they're all owned by root.

How can i make every file in there my own? (pricechild)

I can't be bothered to open nautilus as a root user and change the permissinos for every single file.

Thanks, Pricey

---

### Post by mo_x on 2005-10-30
Try the following command froma terminal in your home directory:
sudo chown -R pricechild .doom3

---

### Post by PriceChild on 2005-10-30
Changed it to
```
sudo chown -R pricechild:pricechild .doom
```
To get it to change the group as well.
He he might be starting to get the hang of the linux terminal :P

Anyway, it's worked and changed every file's permissions!

I've also noticed that one of the files in there which saves the cd key has been made writable by me so i don't have to keep putting in the serial at each launch! :D

Thanks guys, i love Ubuntu :D

---

