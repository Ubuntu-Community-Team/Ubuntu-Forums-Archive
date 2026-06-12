---
title: "root password (I know about sudo and everything)"
date: 2009-01-17
forum: General Help
---

### Post by flyvin on 2009-01-17
I was in a big hurry and had to shut down my computer by just pressing the button. I know this isn't a good thing to do, but my comp was frozen. When I tried to start it up it said unclean shutdown. It was about 90 percent done when it had a weird error and said it needed my root password. I tried my normal password but it didn't work. I have never made a root password on my computer and I have no idea what it is. All the things I could find have just said ubuntu doesn't need one and just use sudo. I can't start ubuntu and now I have to use Windows:mad::mad::mad::(! HELP!

---

### Post by DeMus on 2009-01-17
> **flyvin said:**
> I was in a big hurry and had to shut down my computer by just pressing the button. I know this isn't a good thing to do, but my comp was frozen. When I tried to start it up it said unclean shutdown. It was about 90 percent done when it had a weird error and said it needed my root password. I tried my normal password but it didn't work. I have never made a root password on my computer and I have no idea what it is. All the things I could find have just said ubuntu doesn't need one and just use sudo. I can't start ubuntu and now I have to use Windows:mad::mad::mad::(! HELP!

Maybe this is too simpel:
Did you try typing nothing, since you did not make a password for root. Ubuntu does not need a root password because it works different from other distro's.

---

### Post by flyvin on 2009-01-17
Yeah, I tried typing nothing, root, sudo, su, my real password, password and a few others.

---

### Post by DeMus on 2009-01-17
> **flyvin said:**
> Yeah, I tried typing nothing, root, sudo, su, my real password, password and a few others.

Okay, next step.
When the computer boots you get a list of OS's to choose from. Choose the second one, which says recovery mode and try to boot it.
When it does boot completely, then exit the normal way and boot the normal OS.

---

### Post by flyvin on 2009-01-17
> **DeMus said:**
> Okay, next step.
When the computer boots you get a list of OS's to choose from. Choose the second one, which says recovery mode and try to boot it.
When it does boot completely, then exit the normal way and boot the normal OS.

It did the same thing on recovery mode, I restarted it and same thing.

---

### Post by flyvin on 2009-01-17
Also, the error says:

```
UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
          (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sdb1: 93% (stage 4/5, 395/611)

[COLOR="Red"]*[/COLOR] An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read only mode. 
[COLOR="Orange"]*[/COLOR]
a maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
Give root password for maintenance shell and restart the system.
Dive root password for maintenance(or type Control-D to continue):
```

When I press CONTROL-D it restarts.

---

### Post by Aualin on 2009-01-17
Type in your root password
And then run the commad
```
fsck -C -f /dev/<hard drive>
```
If you know what your hard drive is named in Linux replace <hard drive> with that. Otherwise try sda1, sda2 and so on. (Also hda1 and so on.)

---

### Post by flyvin on 2009-01-17
> **Aualin said:**
> Type in your root password
And then run the commad
```
fsck -C -f /dev/<hard drive>
```
If you know what your hard drive is named in Linux replace <hard drive> with that. Otherwise try sda1, sda2 and so on. (Also hda1 and so on.)

My problem is that I dont know my root password, I never made one and its not my main account password

---

### Post by eatberrys on 2009-01-17
Can you boot in to recovery mode ?

if so ```
passwd root
```might help

---

### Post by mali2297 on 2009-01-17
Do you have the Ubuntu CD available? If so, use that to run Aualin's command. You will need to run the command with *sudo* in front.

---

### Post by flyvin on 2009-01-18
> **mali2297 said:**
> Do you have the Ubuntu CD available? If so, use that to run Aualin's command. You will need to run the command with *sudo* in front.

YEAAAHHHHHHHH!!!:):P:P:P:guitar:
Thanks that worked.

---

