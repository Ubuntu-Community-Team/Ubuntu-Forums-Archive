---
title: "access denied on sudo-apt get update"
date: 2009-01-18
forum: General Help
---

### Post by dogafin on 2009-01-18
dogafin@dogafin-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
dogafin@dogafin-desktop:~$ 


is this bad?

my pc booted and ubuntu wont start, it is forcing an fsck/dev/sda1
i have come across this problem before and wrote down a terminal command on a piece of paper to type sudo blkid, restart, and if its still a no go, to boot with live cd and do an fsck there.

well i was going to boot to cd, but before doing this i went ahead and tried if the pc will boot up, and it did. 

on my piece of paper, another recommendation was written to try and get updates. so when i typed apt-get update i got this message.

no telling if my pc will act up again. but as of now its doing okay. i also need to mention i have deleted an old kernel just a few hours ago.


---------
running ubuntu 8.10

---

### Post by tech0007 on 2009-01-19
Open a terminal and run:

```

ps ax | grep apt

```

If you get an output, that means cron is running the autoupdate.

---

### Post by virtuallinux on 2009-01-19
I usually get an error similar to that if I try and update while a package manager (add/remove or synaptic) is already running.

---

### Post by dogafin on 2009-01-19
> **tech0007 said:**
> Open a terminal and run:

```

ps ax | grep apt

```

If you get an output, that means cron is running the autoupdate.

dogafin@dogafin-desktop:~$ ps ax | grep apt
 6029 pts/0    R+     0:00 grep apt

---

also ive gotten something very interesting when i tried to turn on firewall:

dogafin@dogafin-desktop:~$ ufw enable
ERROR: You need to be root to run this script

---

### Post by abhilashm86 on 2009-01-19
when you are runnibg synaptic package manager or any application download,usually you can't run an update,as some modifications may affect the downloading file.

---

### Post by dogafin on 2009-01-19
> **virtuallinux said:**
> I usually get an error similar to that if I try and update while a package manager (add/remove or synaptic) is already running.

nothing else is running when i got this error. so there must b something wrong. :(

---

### Post by theWrkncacnter on 2009-01-19
You have to run the update command as root, using the sudo command. Try ```
sudo apt-get install update; sudo apt-get install upgrade
```

You can also apply updates with the gui Update Manager of course.
If that still doesn't work, post your output and we'll try to figure it out.

---

### Post by dogafin on 2009-01-19
> **theWrkncacnter said:**
> You have to run the update command as root, using the sudo command. Try ```
sudo apt-get install update; sudo apt-get install upgrade
```

You can also apply updates with the gui Update Manager of course.
If that still doesn't work, post your output and we'll try to figure it out.


wow thank you! i guess terminal is acting "normal". ive typed sudo and it did search for updates w.c it didnt find any eheheh.. but its just weird cause i didnt have to type sudo before when i was running 8.04

---

### Post by theWrkncacnter on 2009-01-19
Hmm, it's strange it let you use apt without being root 0.o
Heh but anyway, just in case it's not clear the "update" command finds the newest updates and the "upgrade" command installs them. Both are necessary for updating, if you're using the terminal.

---

