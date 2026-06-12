---
title: "cannot login to user DE; setuidgid not found"
date: 2012-01-03
forum: Desktop Environments
---

### Post by Joutro on 2012-01-03
I'm running Ubuntu 11.10 and it has been working very well for my old Dell P4.

Recently I did a number of tweaks that I cannot remember where I found the instructions. They are: 

1. adding certain applications to autostart. 
1.1 I wanted TeamViewer to start up at boot (rather than just upon logging in my normal user desktop).

1.2 adding a login certificate for sshd

item 1.2 worked  fine  but the following problem developed after  i rebooted:

now i cannot log in to my normal user account. it does not matter what desktop I try (i had been using KDE. 

upon entering the user login, briefly various logs flash on the screen but it returns to the login GUI. the text disappears so fast i cannot read much of it, but the last line is:

exec 21: setuidgid: not found

after this problem, i was still able to ssh into the machine for that user. I was also able to login locally as root (I had given root a password using the live cd.)

I suspect that my .profile or some other config file is scrogged, but I don't know where to look. I would like to know if the user profiles are backed up so that i can restore a previous version.

I thought i would try using the live cd to reinstall/upgrade but i kept my /home partition and directory intact. I used the mint 12 live cd and selected "upgrade to Ubuntu 12" (yes that is actually what the installer said; I assume it meant mint 12). 

Incidentally, at the end of the intall, it reported that 'some applications could not be saved/upgraded"

basically the login problem remains, but now i can no longer ssh into the machine; i guess the ssh config was overwritten.

---

