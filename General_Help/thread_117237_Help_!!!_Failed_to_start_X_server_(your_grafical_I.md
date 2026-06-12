---
title: "Help !!! Failed to start X server (your grafical Interface)"
date: 2006-01-14
forum: General Help
---

### Post by iraklirost on 2006-01-14
had a problem during the booting my ubuntu checking Root file system
Fsck faild please repair manually

so wrote command: fsck -y 

but now my OS has other problmes:

Failed to start X server (your grafical Interface)
fatal server error(cannot open log file /var/log/Xorg.0.log )

I wrote in terminal:
sudo dpkg-reconfigure xserver-xorg
but it is sayng me:
debconf: DbDriver “config”: couldn’t open /var/cache/deconf/config.dat 

what can I do?

---

### Post by Mr_Grieves on 2006-01-14
Sounds serious..

What does this show?

```

ls -la /var/log/Xorg.0.log

```

If you run the Xorg start command with sudo? What happens then?

Cross posted: 
This thread: [http://www.ubuntuforums.org/showthread.php?t=117237](http://www.ubuntuforums.org/showthread.php?t=117237)
Same thread: [http://www.ubuntuforums.org/showthread.php?t=117233](http://www.ubuntuforums.org/showthread.php?t=117233)

---

### Post by iraklirost on 2006-01-15
> =Mr_Grieves]Sounds serious..

What does this show?

```

ls -la /var/log/Xorg.0.log

```



ls: /var/log/xorg.0.log  no such file or direcotory

in var directory I have only:
/cache /games /lib /lock /mail /opt /run /www

---

### Post by localzuk on 2006-01-15
It looks like some part of your HDD was damaged. You should have a directory called log in the var directory. I personally would advise a re-install.

---

### Post by iraklirost on 2006-01-15
I could reinstall but I have some documents in it I don't want to lose it

tell me please from the terminal how can I coppy my documents from the network to other copputer or how to write in CD

---

