---
title: "PlayStation Portable - Problems with Ubuntu"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Nomearod on 2005-11-01
Hi, i have a PSP and i'm having some problems with it... I can connect the PSP to the PC, and Ubuntu recognise it, but I only can see the files that I have in the memory stck and copy them to the pc. When I try to delete some files or pass some files to the console, it doens't do it...

For example, if I delete a file, the file desapear but the free space doens't change, and when I connect the psp to Windows, I see a new folder called " trash - Username" with the deleted file...

Thanks in advance :KS

---

### Post by Hairy_Palms on 2005-11-01
that means your just sending things to the wastebasket, go to nautilus and ge "Edit->Prefereances" then the behaviour tab and tick the "include a delete command that bypasses wastebasket. then just right click and delete the files.

---

### Post by Nomearod on 2005-11-01
[QUOTE=Hairy_Palms]that means your just sending things to the wastebasket, go to nautilus and ge "Edit->Prefereances" then the behaviour tab and tick the "include a delete command that bypasses wastebasket. then just right click and delete the files.[/QUOTE]


It didn't worked... I deleted some files ( .MP3 ) and the free space didn't change. I also tryed to pass a file to the MUSIC folder but the PSP saied that the file is corrupted ( and it isn't ).:???:

---

### Post by Saotome on 2005-11-01
Had a similar "problem" with my mp3 player. 

Maybe you should delete the files from the ".Trash" folder. Press "Ctrl H" and that hidden folder will appear on Nautilus. Remove it and the free space will change.

---

### Post by Nomearod on 2005-11-01
[QUOTE=Saotome]Had a similar "problem" with my mp3 player. 

Maybe you should delete the files from the ".Trash" folder. Press "Ctrl H" and that hidden folder will appear on Nautilus. Remove it and the free space will change.[/QUOTE]

The Trash folder doesn't appear in Ubuntu, but in Windows it appear and isn't hidden. The problem is that I can't even pass files to the PSP... It's like " read only ".:???:

---

### Post by Nomearod on 2005-11-04
Anyone can help?

---

### Post by timeoff on 2005-11-04
After deleting a file on the PSP, select "show hidden files" on the browser menu and you will find a .Trash folder on the PSP. Delete the file from the .Trash folder. The file is not deleted until the local PSP .Trash is emptied.

Use the above procedure to remove any corrupt files which you have copied over to the PSP. 

Files you have copied over to the PSP will show up as corrupt unless you use the unmount command before disconnecting the PSP. To unmount the PSP before disconnecting, right-click on the PSP icon on the desktop and select unmount. You need to use the unmount option to sync the files on the PSP after copying.

T

---

### Post by Quartus on 2005-11-04
[QUOTE=timeoff]After deleting a file on the PSP, select "show hidden files" on the browser menu and you will find a .Trash folder on the PSP. Delete the file from the .Trash folder. The file is not deleted until the local PSP .Trash is emptied.

T[/QUOTE]
Exactly, remove the files, press Ctrl+h, remove the .Trash-user directory and you're fine.

EDIT: My english...

---

### Post by Quartus on 2005-12-15
[QUOTE=Nomearod]Hi, i have a PSP and i'm having some problems with it... I can connect the PSP to the PC, and Ubuntu recognise it, but I only can see the files that I have in the memory stck and copy them to the pc. When I try to delete some files or **pass some files to the console, it doens't do it**...
[/QUOTE]
Does anyone have a solution on this matter?

---

### Post by Trab on 2005-12-15
when you delete a file off the card try using ctrl+del
it will actually delete the file instead of moving it to the trash...
good luck!

-Trab

---

