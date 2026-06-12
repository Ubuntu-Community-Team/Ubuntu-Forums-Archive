---
title: "&quot;Conversation with su failed.&quot;"
date: 2005-08-17
forum: Desktop Environments
---

### Post by Jaristr on 2005-08-17
Hi. 
I just installed kubuntu but when I try to launch kynaptic and enter the password a message box saying "Conversation with su failed." pops up.
I have used ubuntu before in other machine and there is dual boot with mandrake on this one. 
Kubuntu's home directory is mounted to the same partition where mandrake's home is mounted. Could this be the problem?
I know that su is for changing the user and in console it works just fine.

Thanks.

---

### Post by Juergen on 2005-08-17
AFAIK they should use 'kdesu' in the menus.
Try that in a terminal, maybe you get more info.

Oh, and it may be that your users have different user-ids in the two Linuxes. 
You would have to change one.
What says 'ls -l' in your $HOME to user and group of the files?

---

### Post by Jaristr on 2005-08-18
Thanks for the help Juergen.
kdesu is found when used in console...
And this is what "ls -l" gives:
drwxr-xr-x  65   501   501 4096 2005-08-18 16:23 jari
drwxr-xr-x   8 kjari kjari 4096 2005-08-18 16:31 kjari
drwx------   2 root  root  4096 2005-06-14 16:26 lost+found

kjari is the kubuntu user account and jari is for mandrake.

---

### Post by Juergen on 2005-08-18
Seperate $HOME are OK, you don't need to change one user, then.

Hm, if it works from terminal, but not from the menu... dunno :-(
Maybe look at the properties of the menu-entry for funny extra-parameters or something.

---

### Post by Jaristr on 2005-08-18
[QUOTE=Juergen]Seperate $HOME are OK, you don't need to change one user, then.

Hm, if it works from terminal, but not from the menu... dunno :-(
Maybe look at the properties of the menu-entry for funny extra-parameters or something.[/QUOTE]

Well kynaptic (the packet manager) doesn't start from the terminal. but su and kdesu work from terminal. 
I viewed  the kynaptic menu entry and there aren't any arguments...
And it's not just kynaptic but all programs that require root access - unless used from terminal.

Thanks for the help though.

Edit; I reinstalled kubuntu and it works now.

---

### Post by Julio Ferrari on 2005-09-14
I had the same problem with Kubuntu ...  not just to run commands as root, but it fails even when trying to RUN AS the current logged in user. Seems that no authentication is working from inside KDE interface. It generates entries on Authentication LOG.
   Every attempt generates 2 auth log entries.
   Reinstalling is the only way to solve it ?

---

### Post by Julio Ferrari on 2005-09-14
Forgot some info ...  this is with Kubuntu 5.10

---

### Post by agm642 on 2005-09-14
I think the menus use sudo... Try the instructions here:
[http://ubuntuforums.org/showthread.php?t=62379](http://ubuntuforums.org/showthread.php?t=62379)

---

