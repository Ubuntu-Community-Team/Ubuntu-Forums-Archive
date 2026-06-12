---
title: "Help with permissions"
date: 2009-03-31
forum: General Help
---

### Post by Wired16 on 2009-03-31
I was trying to protect some files I have and i came across the cmd
sudo chown -R root:root /path/to/folder and now I can't even get on them, I am an admin and i know the root pwd but i cant open them under "zack" (my user) and i cant login to root from the login screen... is there anyway i can change it to where only user zack can access that folder/files or a way to login to root and change the permissions? 

Thanks

---

### Post by James_Lochhead on 2009-03-31
sudo chown -R zack /path/to/folder

---

### Post by drs305 on 2009-03-31
First, be very careful using "sudo chown" as one extra space in the destination could trash your entire system ( /home... vs / home...).

If I understand what you did, change the ownership back to yourself and then set permissions:
```

sudo chown -R zack:zack /path.to.folder
chmod -R 700 /path.to.folder

```
700 will allow read/write/execute permissions only for you.

*Edit: Typo fixed, thanks James.*

---

### Post by James_Lochhead on 2009-03-31
The root user is a security feature to stop you and malware from mucking up your computer. Changing the owner to root in this circumstance is protecting you from malware but also stopping you from viewing the files.

---

### Post by James_Lochhead on 2009-03-31
> **drs305 said:**
> 
```

sudo chown -R zach:zach /path.to.folder

```


Change "zach" to "zack" though.

---

### Post by pro003 on 2009-03-31
Ok. The simple way:

Open terminal and type:

```
gksu nautilus
```

enter root passwd

You'll get a new window with root privileges. 

go to the folder's properties and you can under "permissions" se/protect access / read or write / same as for group, etc. 

Close nautilus, and there you go.

I would not recommend you to login as root ever, but only as user and use root privileges only when needed.

---

### Post by Wired16 on 2009-03-31
Ah Thank you very much! First time using ubuntu and I love it so far :D

I will now be way more careful with cmds i use

---

### Post by James_Lochhead on 2009-03-31
> **Wired16 said:**
> Ah Thank you very much! First time using ubuntu and I love it so far :D

I will now be way more careful with cmds i use

Be especially careful of anything involving sudo. This command allows you to execute another command a super user, hence you can screw up your system with it. 

99.9% of commands users post are well meaning, however they are not all so well meaning. For example, **DO NOT EVER EVER** use the command sudo rm -r -f / if you see it. That command attempts to remove every file on your Ubuntu system.

---

