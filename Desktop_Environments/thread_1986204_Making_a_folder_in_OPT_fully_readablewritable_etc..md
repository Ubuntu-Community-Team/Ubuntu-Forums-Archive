---
title: "Making a folder in OPT fully readable/writable etc."
date: 2012-05-24
forum: Desktop Environments
---

### Post by Pally1 on 2012-05-24
Greetings!
I have some stuff installed in OPT where i need to constantly change files and add new ones, create folders and so on. System wont allow me to do it through user interface.

How can i make this folder permanently open to for everything? thanks!

---

### Post by roelforg on 2012-05-24
chmod 777 it (assuming there aren't permission sensitive files there)?

---

### Post by Pally1 on 2012-05-24
> **roelforg said:**
> chmod 777 it (assuming there aren't permission sensitive files there)?


I simply need to have su rights in that folder all the time, will chmod 777 do that?


How do i enter root directroy through command line or something?

---

### Post by roelforg on 2012-05-24
> **Pally1 said:**
> I simply need to have su rights in that folder all the time, will chmod 777 do that?

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Pally1 on 2012-05-24
> **roelforg said:**
> [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


That does not help me, bacuse i dont know how to get the console to root directory, since that is where opt is.

---

### Post by roelforg on 2012-05-24
> **Pally1 said:**
> That does not help me, bacuse i dont know how to get the console to root directory, since that is where opt is.

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)
(don't let the name fool you, it's about the stuff you need to know)

---

### Post by wojox on 2012-05-24
Use sudo to edit the files [RootSudo]("https://help.ubuntu.com/community/RootSudo")

Or like roelforg stated change the permission on the folder.

---

### Post by Pally1 on 2012-05-24
Ok liets do this again, ive recently switched to kubuntu from windows and  installed LAMPP to do some website stuff. For the moment, i cant do anything at all with it because system wont let me create folders in htcdocs or edit xamp settings or do anything else exept just looking at the folders!

How do i do anything at all? And no more alien stuff please :D

---

### Post by ottosykora on 2012-05-25
but did you try to chmod 777 as you were told to do? 

In ubuntu, all operations which you need to do as root, you simply set sudo in front of that and it works.
So if you make sudo chmod 777 , then you have what you want. Where di you find the problem?

You could also create folder as you , as user and the do all inside as user.

and since roelfrog gave you the advise which you refuse to read, here again:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by LewisTM on 2012-05-25
Easiest would be to launch a file manager with sudo/kdesudo like

[FONT="Courier New"]kdesudo dolphin[/FONT] (for a GUI file manager) or
[FONT="Courier New"]sudo mc[/FONT] (for text-mode Midnight Commander)

The file managers will gain superuser privileges i.e. total control. If you launch files with their associated application in Dolphin (e.g. Kate text editor) the app will also inherit superuser privileges so the files will be editable.

If you go the mc way you will notice from the command prompt that you are now functionnaly logged in as **root**. Press Ctrl-O to toggle the file panels and view the terminal output.

The command [FONT="Courier New"]sudo chmod -R 777 </opt/directory> [/FONT]would also work but I fear any newly created files would get default permissions (644) which means that if they were created by a system service they will not be writable by a normal user. You could get around that by setting a system file creation umask of 000 but that is unsafe.

Cheers!

---

