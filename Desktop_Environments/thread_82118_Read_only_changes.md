---
title: "Read only changes"
date: 2005-10-25
forum: Desktop Environments
---

### Post by zilver on 2005-10-25
I installed kismet and now i need to change a config file in /etc/ (btw i started using linux for 1½h ago) but it say i can't change the file i need to change to get it to work

how do i untap the read only mark, it says "Your not the owner you cant change these.. blap blap" when i right click em. so plz help me it must be pretty simple bbut i cant work this out thx in advance

Zilver

---

### Post by endersshadow on 2005-10-25
[QUOTE=zilver]I installed kismet and now i need to change a config file in /etc/ (btw i started using linux for 1½h ago) but it say i can't change the file i need to change to get it to work

how do i untap the read only mark, it says "Your not the owner you cant change these.. blap blap" when i right click em. so plz help me it must be pretty simple bbut i cant work this out thx in advance

Zilver[/QUOTE]

So long as you know what you are doing, and only then, you can do the following:

```
sudo gedit /etc/kismet.conf
```

Where kismet.conf is the name of the config file.  This will open it up in the text editor and give you the proper permissions to edit the file.  Make sure you know what you're editting and why you're editting it that way.  sudo is a great tool, but if you don't know what you're doing, you can really screw up your system.

---

### Post by zilver on 2005-10-26
Thx alot man kismet still aint working but got to the next bug :P

Zilver

---

### Post by endersshadow on 2005-10-26
[QUOTE=zilver]Thx alot man kismet still aint working but got to the next bug :P

Zilver[/QUOTE]

Quite welcome.  Let me know if I can be of anymore help.

And I just realized that I didn't explain what that command did (bad me!).  It's important to know *why* you're doing a command and not just when to do the command, so I'll break it down...it's Hammertime:

sudo means "superuser do," basically, it grants you temporary superuser (otherwise known as "root") privileges to files and commands.  This is what gave you permissions to edit the file.

gedit tells the computer to open up that lovely GUI text editor that can also be found in Applications>Accessories.

And now you know, and knowing is half the battle :-D

---

