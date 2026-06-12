---
title: "Quake 4 as user?"
date: 2005-10-21
forum: Gaming &amp; Leisure
---

### Post by veratyr on 2005-10-21
I can't seem to run quake 4 without using sudo. I get the following:

file system initialized.
---------------------------------------------
TODO: Sys_SetClipboardData
********************
ERROR: Couldn't load default.cfg  -  Check your working folder.
********************
Unknown command 'vid_restart'
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg  -  Check your working folder.

---

### Post by seethru on 2005-10-21
[QUOTE=veratyr]I can't seem to run quake 4 without using sudo. I get the following:

file system initialized.
---------------------------------------------
TODO: Sys_SetClipboardData
********************
ERROR: Couldn't load default.cfg  -  Check your working folder.
********************
Unknown command 'vid_restart'
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg  -  Check your working folder.[/QUOTE]

That sounds like you haven't copied the .pk4 files from the windows cd.

---

### Post by veratyr on 2005-10-21
Well I have, because I can play the game by doing "sudo quake4". My question is how can I get it to run by just using "quake4"?

---

### Post by ltmon on 2005-10-21
[QUOTE=veratyr]Well I have, because I can play the game by doing "sudo quake4". My question is how can I get it to run by just using "quake4"?[/QUOTE]

Guessing here... but what are the permissions set on the .pk4 files?

L.

---

### Post by synrat on 2005-10-21
check the permissions of .quake4  directory. if you first launched it with sudo,
then it was created with root as owner and you can't write to it.

---

### Post by GameGod on 2005-10-21
Yeah, I had this problem. I was also unable to save games...

Turns out my /home/$user/.quake4 directory was owned by root for some reason... I just changed the permissions of everything in it to be owned by me...

chown [user] ~/.quake4
chown [user] ~/.quake4/*
You might need to change the permissions of the two directories inside the .quake4 one too (pb and q4base...)

:)

---

### Post by veratyr on 2005-10-21
got it working. I had to change the permisions of some of the pak files in /usr/local/games to get it to work.

---

### Post by crane on 2005-11-11
[QUOTE=veratyr]got it working. I had to change the permisions of some of the pak files in /usr/local/games to get it to work.[/QUOTE]

Tahts odd. how were the permissions set? I installed Q4 as root and then run as user with no problems.

---

### Post by maxarsha on 2008-05-20
i experienced same problem,
but i just run the game from terminal, it works... no default.cfg problem,

---

