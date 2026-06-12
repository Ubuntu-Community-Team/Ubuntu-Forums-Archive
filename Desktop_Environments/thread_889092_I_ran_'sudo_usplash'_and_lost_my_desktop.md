---
title: "I ran 'sudo usplash' and lost my desktop"
date: 2008-08-13
forum: Desktop Environments
---

### Post by adept_king on 2008-08-13
long story short, i no longer have access to my own documents, pictures, etc folders.

and the desktop that gnome used to point to is also under lock and key.  my new desktop is blank.

my panels are still intact, but i locked myself out of everything.

i have admin privilege, but somehow ubuntu forgot that i am supposed to have access to my own data.

(background: i got stuck in usplash so i forced a reboot by powering down. i still have admin privilege but linux cant see the connection between my user name and my user name's stuff.)

----


okay, I finally found out about permissions, and went to the home folder and gave myself my permissions back and applied full access to all files and folders beneath.

my desktop reappeared after reboot, but at the login screen I got this message:

"user's $HOME/.dmrc file is being ignored"
prevents default session and language from being saved.
file should be owned by user and have 644 permissions.
user's $HOME directory must be owned by user and
not writable by others."

which led me here:

[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

---

