---
title: "I need help"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by Psyco_Chipmunk on 2007-08-07
I just downloaded a thing that makes it possible to play enemy territory with bots.  It says that i have to extract the file into the enemy territory folder, but whenever i try to do this, it says that i dont have the right permissions to do it!  How do I do it then?  :(   Any help would be awesome!  :)

---

### Post by cogadh on 2007-08-07
Use sudo to run the extract command.

---

### Post by Psyco_Chipmunk on 2007-08-07
ok, how do i do that?  the thingy i downloaded is on the desktop and its called:  wolfbot11.0-linux.zip and the folder where i want it is: /home/luke/enemy-terrotpry      


Could you write the thing I have to put in the terminal?   please?  :)

---

### Post by Psyco_Chipmunk on 2007-08-07
woops.   it's.   /home/luke/enemy-territory

---

### Post by cogadh on 2007-08-07
Well, you should have permission to the folder you want to put it in already. That folder is part of your home directory (if you are "luke") and you should have full permissions to everything in your own home directory. If you look at the permissions on the target directory (right-click and select Properties), are they set to read only? If it is, just change your permissions to read and write access then you should be able to extract the files into the directory without using sudo.

---

### Post by Psyco_Chipmunk on 2007-08-07
Well, this error message says that I can't move this file because I don't have permission; because I'm not the owner, but I am the owner! How do I change this file's "permissions" so that I have control over my own computer? Thanks :>)

---

### Post by Psyco_Chipmunk on 2007-08-07
I copied the file and pasted it on my desktop, creating a non-locked file which I was able to put into my Enemy Terr. file, but now it's not showing on my "mods" window? Do you know what I'm doing wrong? Thanks

P.S. These are the directions the website gave me:

"Linux :
Extract the ZIP archive to your root RTCW folder, usually located at /usr/local/games/wolfenstein."

---

