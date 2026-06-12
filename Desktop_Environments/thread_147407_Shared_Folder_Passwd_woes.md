---
title: "Shared Folder Passwd woes"
date: 2006-03-20
forum: Desktop Environments
---

### Post by bluemike807 on 2006-03-20
I have two machines on my network, running Ubuntu and Windows XP respectively. I want to set it up so each can view the other's shared directories.

Using Ubuntu's simple enough shared folder interface with System > Admin > Shared Folders, I've specified the directories on my Ubuntu machine to be shared.
I can *see* the machine from windows, but when I try to access the directory I get a password prompt which, no matter what I enter, wont grant me access.

I've poked around in the smb.conf file but cant find anything to kill this prompt (even if it worked, I dont want to have to enter the username/pass every time I go between machines).

Can someone tell me how to fix it so I can access the shared folders quickly and without this prompt?

Thanks

---

### Post by dermotti on 2006-03-20
Ide be interested in this info also. Ive only had luck with Samba using SMB4k, but i hate installing all those KDE libs just for one app.

---

### Post by outofnicks on 2006-03-20
Myself also, I get multiple login prompts after a timeout of a few minutes.
For the initial login, if I double-click on the desktop icon for the shared folder instead of in the file manager window, it works OK without the multiple logins.
But the short timeouts are annoying, to say the least!

---

### Post by bluemike807 on 2006-03-20
*Bump*
Three people have expressed interest in this issue, but noone's offered any help - cmon, someone out there has to have a solution, or at least a theory

---

### Post by bigscience on 2006-03-21
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

Yours was my situation for a few days until I was pointed at this link.  Follow the instructions.  Despite sharing the folder, you need to tell the samba conf which users may connect to your shares and what permissions you grant them.

---

