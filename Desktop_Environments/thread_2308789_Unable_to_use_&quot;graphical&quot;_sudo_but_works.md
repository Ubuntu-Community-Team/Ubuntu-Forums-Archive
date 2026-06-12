---
title: "Unable to use &quot;graphical&quot; sudo but works fine in terminal"
date: 2016-01-05
forum: Desktop Environments
---

### Post by Greblak on 2016-01-05
I can sudo in terminal, and start programs with from the terminal with sudo and perform administrative duties.
However if I don't, and they ask for the password, for example in GParted or Ubuntu Software Center, I can not successfully approve the request with my password.
Often I can't sudo these apps because they specifically ask for the sudo pwd. The application seems to fail.

This happens on a single user, on XFCE and Gnome 3.

I believe I started noticing it after I did some funky stuff to my home dir. I installed Ubuntu on a too small partition. Encryption was eating up space I didn't have, and I had to move my /home/user folder and remove encryption. I successfully copied rights back to a new user(but with the same username) and symlinked /home/user to a different disk following a couple of guides I found. 

My explanation of all this is that the GUI auth method uses some hash connected to a GUID to the username as well as the password whereas sudo does not? 
I am very little familiar with the inner workings of Linux authentication, but this little problem is starting to get on my nerves a bit!

Any ideas? Any pointers in the right direction is appreciated!

---

### Post by wyliecoyoteuk on 2016-01-05
try using "gksudo" in a terminal, and you might get an error message that will give you a clue.
e.g.
gksudo nautilus
Or gksudo thunar

---

### Post by ajgreeny on 2016-01-05
You should **NEVER USE sudo FOR GUI APPLICATIONS**; if you do it is possible that you may lock yourself out of the system as ownership of files and folders in your /home may become owned by root, not by you as user.  Always use gksudo or gksu instead.

See:-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
and 
[http://ubuntuforums.org/showthread.php?t=2308613](http://ubuntuforums.org/showthread.php?t=2308613)
for more information and discussion.

---

### Post by wyliecoyoteuk on 2016-01-05
I think he is actually having problems with gksudo, which is why I suggested running it in a terminal to see if he gets any error messages.

---

### Post by yetimon_64 on 2016-01-06
> **ajgreeny said:**
> You should **NEVER USE sudo FOR GUI APPLICATIONS**; if you do it is possible that you may lock yourself out of the system as ownership of files and folders in your /home may become owned by root, not by you as user.  Always use gksudo or gksu instead.

See:-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
and 
[http://ubuntuforums.org/showthread.php?t=2308613](http://ubuntuforums.org/showthread.php?t=2308613)
for more information and discussion.

sudo with the -H switch will work as it sets the correct home environment variable for the root user. This should stop the users home folder or files being altered which is usually the problem with sudo and graphical applications.
 
From "man sudo" ... 
>      -H, --set-home
                 Request that the security policy set the HOME environment variable to the home directory spec&#8208;
                 ified by the target user's password database entry.  Depending on the policy, this may be the
                 default behavior.

Regards, yeti.

---

### Post by Greblak on 2016-01-06
Apparently gksu package was not installed, after installing it, everything seems to work like normal again.
I do not recall uninstalling that by choice!

Possibly corrupted something when moving stuff and changing up user rights causing it to fail somehow?
Strange... But seems to be solved!
Thank you! :)

---

### Post by wyliecoyoteuk on 2016-01-06
gksu was probably not installed, it isn't always required.
Installing it probably reset your HOME environment variable

---

### Post by Greblak on 2016-01-07
Most likely the HOME var. I changed when I messed around with the location but perhaps it didn't propagate to all places that needed it and copy it upon install/config instead of reading it live?

---

