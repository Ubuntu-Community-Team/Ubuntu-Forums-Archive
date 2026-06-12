---
title: "Linux game install question"
date: 2007-03-17
forum: Gaming &amp; Leisure
---

### Post by bo_jo on 2007-03-17
I am new to Ubuntu Linux so I hope this isn't a dumb question.
I downloaded a Linux demo for the game Descent 3.  The file 
name is "descent3-demo-x86.run".
I have no idea how to install/run this game in Ubuntu v. 6.10
Can anyone help me with this?

---

### Post by GiantRobot on 2007-03-17
Usually you should just be able to open up a bash window and get into the directory that you downloaded your file to and type:

```
./descent3-demo-x86.run
```

you also might have to change the permissions on the file before you run it. For example:

```
chmod a+x descent3-demo-x86.run
./descent3-demo-x86.run
```

You also might have to run the installer as root by typing sudo before the run command "./"

Good Luck!

---

### Post by bo_jo on 2007-03-17
Thanks

---

### Post by bo_jo on 2007-03-17
I have another question, I keep getting an error message "permission denied"
even when doing this under a session with temporary root privileges.

user@user-laptop:~$ cd /descent/

user@user-laptop:/descent$ ./descent3-demo-x86.run
bash: ./descent3-demo-x86.run: Permission denied
user@user-laptop:/descent$

user@user-laptop:/descent$ sudo -i
root@user-laptop:~# cd /descent/

root@user-laptop:/descent# ./descent3-demo-x86.run
bash: ./descent3-demo-x86.run: Permission denied
root@user-laptop:/descent# 

Is there anything I'm missing here?

---

### Post by hikaricore on 2007-03-17
```
sudo chmod ugao+xrw /descent/descent3-demo-x86.run
```

See if this helps.  This will allow the file to be read, written, and run by all users.

Only thing I can think of.

---

### Post by bo_jo on 2007-03-17
Thanks for the reply, I finally got the demo game to run
with the command  "sh descent3-demo-x86.run"

---

