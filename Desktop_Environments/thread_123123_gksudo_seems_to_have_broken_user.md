---
title: "gksudo seems to have broken user"
date: 2006-01-29
forum: Desktop Environments
---

### Post by Barnaby on 2006-01-29
Hi all,

I did a couple of customizations after coming across the RootSudo Ubuntu Wiki section. Created  a launcher on the gnome panel that is letting me access nautilus with root rights to change file permissions, delete etc.

However this now seems to have broken my user account - had 5.10 preview installed but since breakage performed a full dist-upgrade.

I seem to have different wallpapers and background colors for two users, being unable to change anything in normal user, don't even get a right click mouse menu after first log in. To get back into what used to be my only account I now always have to access Nautilus with gksudo shortcut on the panel and type the password. Then desktop background will change to what used to be normal user's background.
By all evidence I now seem to have two accounts, a root or power user and a new very restricted account.

Also since recently get an error message on login screen. To the tune of but not exactly "Your $HOME.dmrc file cannot be accessed and is being ignored. You should change permission to user and file permissions to 644."

Where can I find this file? Don't want to reinstall 'cos otherwise no problems.

Thanks.

Edit: Ok I found some other threads with similar problem like [http://www.ubuntuforums.org/showthread.php?p=479186#post479186](http://www.ubuntuforums.org/showthread.php?p=479186#post479186) but I do not seem to have a HOME.dmrc file. Any clues?

---

### Post by Barnaby on 2006-01-29
There it is - damn hidden files. Let's see if getting it down to 644 solves it...

---

### Post by Barnaby on 2006-01-29
Fixed the .dmrc file issue and the error at login screen has now gone.

The other issues still remain though and it seems were not related to the HOME/.dmrc but have to do with gksudo. Any tips from the master roasters?

Thanks.

---

