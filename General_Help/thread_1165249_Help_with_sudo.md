---
title: "Help with sudo"
date: 2009-05-20
forum: General Help
---

### Post by gforster on 2009-05-20
I am setting up a computer lab - switching from Windows 2K. The computer logins are all Student1, Student2, etc. I would like them to login with a simple password - something akin to password1, password2, etc. (not that simple, but for sake of illustration).  I do not want that password to be the sudo password (for obvious reasons), so I thought I would set up the administrator account first, because that is where the sudo password comes from. So I did and then created the user Student1 with a password of password1. I login to the student1 account and try to do an administrative task (apt-get update) where it asks me for my sudo password. I enter my original sudo pass, but it is not accepted. So, I try the passsword1, which is accepted, BUT student1 is not in the sudoers file!

What I want is to be able to run admin tasks with the sudo password without logging out and back in with the administrative account (not root, just the first account). Is there any way to accomplish this?

---

### Post by Titan8990 on 2009-05-20
The only way to use root privs with a user that does not have sudo permission, is with an unlocked root account. Not supported here.

---

### Post by CatKiller on 2009-05-20
> **gforster said:**
> What I want is to be able to run admin tasks with the sudo password without logging out and back in with the administrative account (not root, just the first account). Is there any way to accomplish this?

Yes, with su.

Anything that you do on the command line, you can use su to quickly log on as the first user and then do whatever it is that you need to do.

```
su firstuser
(firstuser's password)
firstuser@localhost:$sudo whatever

```The graphical tools are steadily getting there with using the new framework (PolicyKit?) that lets you unlock the tool using whichever user has admin privileges, but they aren't all there yet. You can still launch the ones that aren't from your su'd terminal with gksudo, though.

---

### Post by DGortze380 on 2009-05-20
Each account can use sudo, they just have varying levels of privledges based on sudoers.

To use an admin function, without enabling root, from a user (student) account, open a terminal and do the following:

```

su <admin username>

```

```

sudo <my command>

```

```

exit

```

---

### Post by sisco311 on 2009-05-20
[uhelp]community/RootSudo[/uhelp]

By default, members of the admin group may gain root privileges.

Remove the accounts from the admin group.

```
sudo delgroup studentX admin
```

You can su to your admin account:
```
su adminusername -
man su
```

---

### Post by albinootje on 2009-05-20
> **gforster said:**
>  So, I try the passsword1, which is accepted, BUT student1 is not in the sudoers file!

Is that user in the group admin or not ?
> 
What I want is to be able to run admin tasks with the sudo password without logging out and back in with the administrative account (not root, just the first account). Is there any way to accomplish this?

If you're working in a terminal, you can do this :
```
su - your-special-username
```, and then : ```
sudo apt-get update
```
If you want to perform GUI operations, install ssh, 
```

sudo apt-get install ssh

```
and do the following (still on the desktop of that non privileged user) :
```

ssh -X -v your-special-username@localhost
gksu synaptic (just an example)

```

---

### Post by gforster on 2009-05-20
thank you!  duh! I've only rarely used su. I never thought about applying it to this. I feel like an idiot, but I thank you for not treating me like one!

---

