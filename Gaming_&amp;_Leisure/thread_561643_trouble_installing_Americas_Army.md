---
title: "trouble installing Americas Army"
date: 2007-09-27
forum: Gaming &amp; Leisure
---

### Post by shorty28898 on 2007-09-27
i followed the way to do it on this page..
[https://help.ubuntu.com/community/AmericasArmy](https://help.ubuntu.com/community/AmericasArmy)
but then this comes up

lindo@ubuntu:~$ sudo sh ./armyops250-linux.run
Password:
sh: Can't open ./armyops250-linux.run

who can help!!??

---

### Post by oerd on 2007-09-27
As** sh** has not been working for me these days i've had to tell the shell that i want the files executed by bash instead of sh, so:
```
sudo bash ./armyops250-linux.run
```
It should also run on it's own if you:
```

sudo chmod a+x armyops250-linux.run
sudo ./armyops250-linux.run
```

---

### Post by monoufo on 2007-09-27
i can't get past the training in that game.  I keep shooting the officers in the head, and they send me to jail, haha.

---

### Post by shorty28898 on 2007-09-29
still not working.. this came up

lindo@ubuntu:~$ sudo ./armyops250-linux.run
sudo: ./armyops250-linux.run: command not found
lindo@ubuntu:~$ sudo chmod a+x armyops250-linux.run
chmod: cannot access `armyops250-linux.run': No such file or directory
lindo@ubuntu:~$ sudo ./armyops250-linux.run
sudo: ./armyops250-linux.run: command not found

i saved it on the desktop, and thats why it would not work.  put it in home folder and it worked.


SOVLED

---

### Post by mudflea on 2007-10-08
right click    "armyops250linux.run" open properties and under permissions make sure  allow executing as file is checked (ticked

---

### Post by Posterus on 2007-10-11
> It should also run on it's own if you:
```

sudo chmod a+x armyops250-linux.run
sudo ./armyops250-linux.run
```

Thanks, that worked great.

---

### Post by artvds2708 on 2007-10-22
Well my .run works.
But when the sprograms starts with the base install, it will not stop.
It just keeos on going for minutes !!
Is this normal ?
Please help

---

### Post by blitzer on 2007-10-22
This is normal :)  The base install should move to let you know it is completing.  When it is installed find an empty server to update your punkbuster or if someone knows an easier way.

---

### Post by de_valentin on 2007-11-25
I have tried in 2 different ways now but I get the same error everytime
[https://help.ubuntu.com/community/AmericasArmy](https://help.ubuntu.com/community/AmericasArmy)
and
[http://ubuntuforums.org/showthread.php?p=3834918#post3834918](http://ubuntuforums.org/showthread.php?p=3834918#post3834918)

and here is the error I get

valentin@valentin:/media/sda4/Downloads$ sudo ./armyops250linux.run
Verifying archive integrity...Error in MD5 checksums: fecac0db78c8a092635af59fa8761528 is different from dc7ebb581249712f797c6d283a8e98a5
valentin@valentin:/media/sda4/Downloads$

how can I fix this?

---

### Post by trstn on 2007-12-01
but what if it keeps repeating it base install? and going up to 100% then resetting and starting again from 05?

---

### Post by theiwaz on 2009-08-24
The repeating base install us completely normal. You just have to ignore it. I've just finished it, and you just have to leave it running.

---

