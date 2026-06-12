---
title: "how to sync  folders between two user accounts?? not exactly sync"
date: 2007-06-04
forum: Desktop Environments
---

### Post by vilto on 2007-06-04
here is my problem ...................
let us say i have two acounts on my ubuntu pc ...................... 
And i installed some application in wine say VC++, in first user account ............... now i dont want to install the VC++ again in the second account ; i want  the second user to be able to use that installed one in first users ....
as u know the softwares installed in wine goes to  ~/.wine /.....    which r different in different accounts

similarly let us say for example firefox ........... i use it in 1st user account make some changes like adding bookmarks or addons some thing like that
now when i open the firefox in second user account it must be able to recognize the changes and vice verse


basically i want to make a dummy settings folder in second user which maps to that in first users and uses its settings................ and when u make any changes in the second users the first accounts settings will also be changed.......

sorry for my bad english :(

plz help i really in need for this........... thanx in advane :popcorn:

---

### Post by xarmian on 2007-06-04
If this is a personal PC and you dont have any fear about permissions you can try to do this by using symlinks..  Basically you would symlink one account's settings folders (such as /home/secondary/.wine) to the settings folder of the other.

*Just a word of warning, this is inherently insecure if this is a multiuser machine, as the settings folder(s) you are using will be world-readable and world-writable..*

The example I'm going to use would assume the settings folder of the user you want to symlink is /home/secondary/.wine and the user you want to link to is /home/primary/.wine and we will use the command line to do everything:

1. Change the permissions settings for the "primary" user's home directory and .wine folder.  We are makng the home folder of the primary account accessible, although it probably is already by default.  We will use permission 755 for the home folder, although 711 will probably work too.  We are then making the .wine folder world-writable (recursively):

> chmod 755 /home/primary
chmod -R 777 /home/primary/.wine

2. Back up your existing .wine settings folder by going to /home/secondary and moving the folder to a new name:

> cd /home/secondary
mv .wine .wine.bak

3. Create a symlink to the .wine settings folder of the primary user account:

> ln -s /home/primary/.wine

Theoretically this would allow our secondary user account to access the settings and modify the settings of the primary user account.  I do not know if this will work for every app, or even any app, so please don't blame me if this doesn't work.  If it doesn't work, go to the /home/secondary folder and "rm .wine", then move the .wine backup back into its original place "mv .wine.bak .wine"

Good luck. :)

-Dave

---

### Post by vilto on 2007-06-05
i tried as u told worked like a charm for many applications ..... thanx a lot :popcorn::p:p

i tried the same thing with crossover office . tht the main thing in after:(
 but i get the following errors when i pressed run windows command  ( see attachments) ................ wht files should i modify in .cxoffice to get it working

---

### Post by xarmian on 2007-06-05
Glad to hear it worked for the most part.. Unfortunately I've never used crossover office so I don't know what's different about it.. That first error message looks like just a permission related error, maybe it's actually checking the owner of the file(s), which seems kind of strange..

Hopefully someone else here knows a little more and can chime in...

-Dave

---

### Post by vilto on 2007-06-06
do anyone know how to solve this problem???

---

