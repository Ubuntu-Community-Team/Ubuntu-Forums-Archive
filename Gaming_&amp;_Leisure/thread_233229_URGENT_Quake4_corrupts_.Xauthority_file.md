---
title: "URGENT: Quake4 corrupts .Xauthority file"
date: 2006-08-09
forum: Gaming &amp; Leisure
---

### Post by ravalox on 2006-08-09
If you install Quake 1.3 it can corrupt your .Xauthority file.  This cost me the ability to do anything of a graphical nature.  I can't seem to divine how to fix it, but if you are using Athlon64 don't install Quake4 without being prepared.  And, can anyone tell me how to fix my .Xauthority file?

---

### Post by User_Program on 2006-08-09
Edit:  One more thing what type of permission do you have for your .Xauthority file in your home dir ?  another thing also can you login as another user? 
Try renaming  .Xauthority in your home dir it's hidden  ..and also there is a patch to the 1.3 its 1.3-2   it solved the problems with smp and 64 bit.  



You can get it here [ftp://ftp.idsoftware.com/idstuff/quake4/linux](ftp://ftp.idsoftware.com/idstuff/quake4/linux)

---

### Post by ravalox on 2006-08-09
I have read and write privleges on it, I am working with the 1.3.2 patch, but the damage is done.  I need to know how to repair the .Xauthority file.

---

### Post by MetalMusicAddict on 2006-08-09
I just installed this patch. I use Xubuntu and I installed with sudo. After I first installed I ran the game with sudo so it created the files in my home dir. (didnt work otherwise) Then I changed the permissions on that directory over to me. So far so good with the 1.3 patch.

---

### Post by User_Program on 2006-08-09
I also had no problem with 1.3 but Im not using the 64 bit kernel. (but having a 64 bit chip..yes)  I ended up updating to the 1.3-2 being that it was a linux patch.

@ravalox I don't know how to repair the .Xauthority file as in going into it and editing things.  I have ran into a similar problem with that file before and renaming it worked for me.  Just a suggestion for a possible fix.

 I don't know if I would blow the horn on Id right away as to say everyone will have problem with Q4 and 64bit

---

