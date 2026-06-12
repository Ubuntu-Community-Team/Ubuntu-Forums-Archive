---
title: "Simple script as a launcher?"
date: 2010-12-15
forum: Desktop Environments
---

### Post by stoopkitty on 2010-12-15
So I wanted to use the command ```
sudo shutdown -c
``` in a shutdown script that launches when I click an application launcher in one of my panels. I need this because I use scheduled shutdowns and I want to be able to cancel them quickly and easily if need be. 

It would be nice to somehow change this so I didn't need to enter my password, but I know it uses sudo and this might be too complicated or impossible. If it's simple enough though, please tell me. 

I don't really know that much about making scripts. What extension do you save them as, do you have to mark them as executable, etc. I basically started out with the bin bash or whatever deal at the beginning and then just put in that command. What else do i need to do? Thanks!!

---

### Post by Krytarik on 2010-12-15
Got one solution (all commands are entered in terminal):

- write a script with only "shutdown -c" in it, I would place it in /usr/local/bin
```
cd /usr/local/bin
sudo gedit shutdown-cancel

```- make it executable
```
chmod +x shutdown-cancel
```- change the owner to root
```
sudo chown root.root shutdown-cancel
```- set the "setuserid"-bit, that means that when the script is run it is run as the owner, in this case: root, you don't have to enter the root-password in this case
```
sudo chmod u+s shutdown-cancel
```- create a launcher to execute that script, I assume you know about that part

EDIT: Oops, I just yet learned that it's not enough to set the SUID for the script alone, it must also be set for the invoked executables, in this case /sbin/shutdown.
That of course is a security risk. You could try to set the group to yours, therefore root must be added to your group, or create a new shared group; and then change the permissions of "/sbin/shutdown" so that other user than the owner and members of the group can't execute it.
```
sudo chmod o-rx /sbin/shutdown
```But I don't know if that entails a problem when trying to shutdown.

You could also try make a copy of /sbin/shutdown, place it somewhere else, set the SUID-bit and execute it instead of the original, but I also don't know if that works.

---

### Post by kerry_s on 2010-12-15
> **stoopkitty said:**
> So I wanted to use the command ```
sudo shutdown -c
``` in a shutdown script that launches when I click an application launcher in one of my panels. I need this because I use scheduled shutdowns and I want to be able to cancel them quickly and easily if need be. 

It would be nice to somehow change this so I didn't need to enter my password, but I know it uses sudo and this might be too complicated or impossible. If it's simple enough though, please tell me. 

I don't really know that much about making scripts. What extension do you save them as, do you have to mark them as executable, etc. I basically started out with the bin bash or whatever deal at the beginning and then just put in that command. What else do i need to do? Thanks!!


just set nopasswd for shutdown in visudo.

example:
sudo visudo

**%admin ALL=NOPASSWD: /sbin/shutdown**

see pic

---

