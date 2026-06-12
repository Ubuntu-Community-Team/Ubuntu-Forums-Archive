---
title: "User rights/ownership all screwed up"
date: 2009-02-27
forum: General Help
---

### Post by evride on 2009-02-27
Earlier today I installed the latest Nvidia driver. Downloaded it off of the Nvidia site, quit X Windows Server, installed it, and started X Windows again. When I got back into X Windows it said my username was "root" not Evan like it should have been. Since then everything has been pretty screwed up. I couldn't start Synaptic with root privileges and I couldn't change the Open With Application on files. I got both those problems fixed. But I have one last problem.

I cannot edit the Applications menu. I right click on applications and click Edit Menu but the program to edit the menu doesn't show up. What do I do?

---

### Post by taurus on 2009-02-27
Boot into recovery mode from GRUB menu and get into root shell.  Then have a look in /home to see who owns your $HOME now.

```
ls -la /home
```

---

### Post by evride on 2009-02-27
thanks taurus, got help on the IRC channel tho. For future googlers who see this:

just open up a command prompt and run

sudo chown user:user -R /home/user
(replace user with your username)

---

### Post by taurus on 2009-02-27
> **evride said:**
> thanks taurus, got help on the IRC channel tho. For future googlers who see this:

just open up a command prompt and run

sudo chown user:user -R **[COLOR="Red"]/home/user[/COLOR]**
(replace user with your username)

That would work but what if /home/user is under a difference name?   Then 

```
sudo chown user:user -R /home/user
```
wouldn't work because your username is Evan while /home/user would be root (/home/root) as you have described in your OP.

---

