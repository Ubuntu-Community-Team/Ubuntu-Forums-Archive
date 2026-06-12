---
title: "How to set a new &quot;home&quot; directory"
date: 2005-08-03
forum: Desktop Environments
---

### Post by alquimista on 2005-08-03
Hi,
I have Kubuntu and I'm sharing a Win32 partition with WinXP. In that partition I have "My Documents" directory; is it possible to set "My Documents"  as my user's home, instead of /home/user?

Thanx,
Guillermo

---

### Post by adwait on 2005-08-03
Sure, In System>Administration>Users and Groups....click on your username and then properties. In one of the tabs (second one I think) you can set the home directory.

---

### Post by SGC on 2005-08-03
[QUOTE=adwait]Sure, In System>Administration>Users and Groups....click on your username and then properties. In one of the tabs (second one I think) you can set the home directory.[/QUOTE]
 That who you do it in Gnome, To do the same in KDE go to:
kmenu -> System -> User Manager(KUser)

Double-click on the user who you want to change the home folder for, and change the forth field (Home Folder) to the new directory.

Also you may want to change the paths for the desktop, autostart, and documents from:
Control center -> System Adminstration -> Paths

---

### Post by adwait on 2005-08-03
Oops.......didn't realise its the Kubuntu forum.......sorry, my mistake.

---

### Post by dare2dreamer on 2005-08-03
depending on the format of your "my documents" partition, you may not wish to use it as your home directory because it probably doesn't support linux permissions fully.

A better solution would be to make a link to your my documents directory in your existing home directory, so that it shows up as a folder in your home dir.

sudo ln -s pathtomydocuments nameoffolderyouwantinhomedir

---

### Post by alquimista on 2005-08-03
I did the change as suggested but now I'm not able to login any more !!!! ](*,) 

Is there a way to change in Consle this setting back to "/home/user" so I can login again???

Guillermo

---

### Post by wrtrdood on 2005-08-03
The login directory is controlled by the sixth field of the /etc/passwd file.  You can edit this file from the console (sudo required) and change that path back to where it was.

  You can change your login directory to nearly anything but, as mentioned, Linux needs to handle the permissions.  You could follow the symbolic link suggestion and use that name in the passwd file field.  Keep in mind that the permissions on the login directory must be owned by that login for it to work properly.

  Even so, the subdirectory suggestion is still the better choice.

---

### Post by alquimista on 2005-08-03
Thank you!!! I got it back working, editing the passwd file. I'll do the link solution.

Guillermo

---

