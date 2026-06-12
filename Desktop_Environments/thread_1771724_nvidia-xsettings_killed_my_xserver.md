---
title: "nvidia-xsettings killed my xserver"
date: 2011-05-30
forum: Desktop Environments
---

### Post by baarn on 2011-05-30
Hey, i tried to get some glx support to my X11/xfce4 so i read some threads and i just wanted to try out nvidia-settings to check out how far i've come. it told me to run nvidia-xconfig (which i did) afterwards X refused to start at all, so i copied back the old xorg.conf.
i know that X has changed a year ago or so and xorg.conf isnt really of any use (so that file is "like" empty, just three lines or so).

whatever, now i cannot login to my old xfce4 environment, i get the loginbox and type in password, after 2 secs i get a black screen with some errors (blinks away after half a sec) a black screen with a cursor and then get back to the login screen... 
i am not really sure wich error log to post, /var/log/xorg.0.log is empty ...

Edit:
i just created a testuser and it works...
i think that narrows down the problem, but actually not for me, i allready opened some of the hidden .X files in /home of my mainuser but have not found any clues to my problem

---

### Post by 3Miro on 2011-05-30
This is an XFCE issue, if you can see the login screen then the Nvidia driver is working fine.

There are couple of things that you can do. It is hard to know which .config file is causing the issues, but you can delete all the config files (anything with .config/xfce4 or xfce4 or xfwm4 or thunar). Don't mess with things like .mozilla as it will erase your settings and bookmarks.

Alternatively, you can get .config (and maybe some other .something folders) from the testuser and overwrite the settings for the original user.

Alternatively: You can move the old /home/your_username folder to a new name:
```
sudo mv /home/originalusername /home/originalusername_backup
```
Delete the original user and then add the user again with originalusername. Then go into /home/originalusername_backup and move .mozilla and whatever Documents/Pictures/Downloads that you may have to the new account.

---

### Post by baarn on 2011-05-30
thanks for the reply
so i deleted that users homefolder (after backing it up)
but that changed nothing
so i deleted the user and readded it (that worked)
and afterwards i copied my complete home folder back

it still works (ok, my desktop config is still ****** up, but maybe thats just some problem chmod/chown will change (i copied everything as root)... maybe it will back-fuckup it again, but then i know what to do.

thank you :)
now i just have to find out how to get that user back into the sudoers, i dont like to use the root account that much...

edit: ok, cp apparently ignores hidden files... good to know, haha
not to bad, system was fresh, only thing lost are some firefox addons... so no problem

---

### Post by 3Miro on 2011-05-30
> **baarn said:**
> thanks for the reply
so i deleted that users homefolder (after backing it up)
but that changed nothing
so i deleted the user and readded it (that worked)
and afterwards i copied my complete home folder back

it still works (ok, my desktop config is still ****** up, but maybe thats just some problem chmod/chown will change (i copied everything as root)... maybe it will back-fuckup it again, but then i know what to do.

thank you :)
now i just have to find out how to get that user back into the sudoers, i dont like to use the root account that much...

You have to add the account to the admin group.

---

### Post by baarn on 2011-05-30
is that group called "admin"?
i am a bit dumb on group management, just added the user to root group. i like having root access, but not for day-to-day usage.

how can i add that user to another group? usermod?
and how can i check in which groups he is and which groups i have on my system. (i am not sure if i maybe forgot to add him to some)

---

