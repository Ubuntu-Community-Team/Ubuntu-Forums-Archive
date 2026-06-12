---
title: "quake 3 permissions"
date: 2007-08-23
forum: Gaming &amp; Leisure
---

### Post by lynryd on 2007-08-23
I've a fresh install of Ubuntu, and been trying all day to get quake3 working properly. Permissions are driving me crazy - I can't change any game settings (and have no sound but I'll deal with that some other time) because I can't write to the damn cfg file.

So I've q3 installed to /home/me/games/quake3 directory. First time I used sudo to install and all the folders were owned by root. I couldn't change the permissions so looked up how to log in as root, and changed them all to belong to me (only user on the machine) but that proved a waste of time. I re-installed without using sudo and the folders now have the correct permissions automatically but I still can't change any settings, and the console still says 'couldn't write to q3config.cfg'.

please help, I've been at this for hours and have had enough searching the net for this. Windows never looked so good as right now :sad:

---

### Post by XTREEM|RAGE on 2007-08-25
This worked for me

sudo chown -hR USERNAME:USERNAME /home/USERNAME/.q3a

It will be hidden, so turn hidden files on. View->show hidden files

source [http://ubuntuforums.org/showthread.php?t=237088](http://ubuntuforums.org/showthread.php?t=237088)

---

### Post by cjl2301 on 2007-08-25
If the above post doesn't work you can try this:

```
sudo chmod -R 777 /home/USERNAME/.q3a
```

---

