---
title: "Administrator account?"
date: 2009-01-19
forum: General Help
---

### Post by sim085 on 2009-01-19
Hi,

I am installing Ubuntu 8.10 Server Edition on Virtual Box. I have reached the point where I am asked for the Name of the user to use the system and the login username and password. 

Now, being relatively new to the whole Linux world, I entered in a dilemma! 

Does a linux installation need to have an administrator account? Or this is already there through the sudo command?

Thanks and Regards,
Sim085

---

### Post by adamlau on 2009-01-19
For all intents and purposes, there is already one through sudo. Name the system anything you want and the user anything other than 'root' :) .

---

### Post by hyper_ch on 2009-01-19
the first user created during install will be put into the "admin" group which means that he can act as root by prepending sudo, gksudo, kdesude with a command.

---

### Post by albinootje on 2009-01-19
> **sim085 said:**
> 
Does a linux installation need to have an administrator account? Or this is already there through the sudo command?


Please look at this :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ubuntu uses sudo.
A lot of other Linux distributions have a root password instead, and use "su" instead of "sudo".

---

### Post by sim085 on 2009-01-19
Hi,

thanks to everyone for the replies :)

My concern comes from the fact that I installed linux with a guest account. I did so because I know I had read somewhere that ubuntu/linux has the sudo account which is like the administrator. 

However after the installation I tried to login with sudo. At that point I discovered I did not have a password for that account. I therefore did some research where they say that you can bind the sudo account with an account created on the OS (or something like that). However being a newby I did not understand much.

Therefore I decided to ask the question here to see what you other people do. 

Thanks and Regards,
Sim085

---

### Post by Iowan on 2009-01-19
As **hyper_ch** mentioned, the first user created (that'd be the one you were asked about) *becomes* the administrator... sort of.  When you log in as that user (hope you didn't name it **sudo**) you can "administer" using the "sudo" prefix (or the others **hyper_ch** mentioned). If you remember the name of the first user, but not the password, see [this]("http://www.psychocats.net/ubuntu/resetpassword") help.

---

### Post by albinootje on 2009-01-19
> **sim085 said:**
>  My concern comes from the fact that I installed linux with a guest account.

Let's assume you meant that you create a "guest" account with the name sim.

However after the installation I tried to login with sudo. At that point I discovered I did not have a password for that account. [/QUOTE]

You would log in as "sim", after successfully logging in you can for example do :
```

sudo nano /etc/fstab

```
to edit the /etc/fstab file as "root".
The password you're being asked for after typing in this command, is the password for user "sim".

Does this make more sense to you ?

---

### Post by Bölvaður on 2009-01-19
> **sim085 said:**
> However after the installation I tried to login with sudo. At that point I discovered I did not have a password for that account.

excuse me but :lolflag: :D hahaha ohhh god. I will try to help you as well as I can, but I really had to get that out of my system... this was too typical of what I would have asked few years ago :)

When you are on a new OS the best advice I have seen is "please unlearn everything you would expect from the others you know"... well unless if they are standardized and unix like. There is no reason having a special account to log in to, to do system changes... unless if you really want one.

Ok, here is what you should read :

Sudo is a command logs you into super user as seen here: (who am i is a command that states what user you are currently)

```
user@tester:~$ **whoami**
***user***
user@tester:~$** sudo** whoami
[COLOR="Silver"][sudo] password for user:[/COLOR] 
***root***
user@tester:~$ whoami
**whoami**
***user***
```

As you can see you are doing commands with the privileged user named superuser aka Root. But you will have to use the sudo command every time you want to let super user doing the command.

You can run any program as root. A beginner like my self would sometimes use ```
gksudo nautilus
``` to do changes to my files without having to call every file I wanted to change as super user (like : gksu gedit /etc/fstab).

The bad thing about that is if you have a user that wishes to install programs via synaptic or add/remove, he'll have to get the super user password for it (you cannot change the system without root privileges, which increases security and stability).

But what you can do is make a special master account (that would be the first one you create from the installation) and perhaps several user accounts with stripped down privileges. System &#8594; Administration &#8594; Users & Groups.


Did that help?
I really do hope so, good luck and all mate.

*added*
Ubuntu is a little different form many other distros as there is only one account created but there are many users. One of those users is Root, another one is you, and a third one is for an instance Games. This is because the OS cannot check if the user is you... but it can run programs which all need to be run with sirtain priveledges or lack of priveledges. I can run many programs as different users at once, as it isnt the account I am logged into.

Well basically... programs are run as users with some rights... like you have to create a special user for the PostgreSQL database.

---

### Post by sim085 on 2009-01-20
Thanks again to everyone for the replies :) I believe things are now starting to get a little bit more clear now. However I still have a few questions to ask. To help myself I installed Xubuntu on a virtual machine. Here I went to the User Settings window. In this screen I can see two users being listed; the user I created during installation ('sim085') and the root user.

Now I click the manage group button and another window is displayed. Here there are listed several groups. However to my surprise I also see listed again my 'sim085' and 'root'. So what does this mean?

From the last post I understand that linux has Accounts (the groups?) and Users. If so then under which account is sim085 listed? Also when we use the sudo command we become the root user, right? So does that mean that I can be more then one user at the same time?

Also reading the contents over here : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) I got another question. Is it only the first account created during the installation which can use the sudo command? Why is this so?

---

### Post by hyper_ch on 2009-01-20
for each user normally also an own group will be created.

---

### Post by albinootje on 2009-01-20
> **sim085 said:**
>  From the last post I understand that linux has Accounts (the groups?) and Users. If so then under which account is sim085 listed? 

Hmm,no. There are users and groups. The word accounts refers to users.
The groups are basically for defining what an user is allowed and what not.
> 
Also when we use the sudo command we become the root user, right? 

Yes.
> 
So does that mean that I can be more then one user at the same time?

Yes.
> 
Also reading the contents over here : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) I got another question. Is it only the first account created during the installation which can use the sudo command? Why is this so?

Yes.
It makes sense because the person doing the Ubuntu administration is likely the sysadmin of the system.
But.. you can create new users and then choose to give them administration rights with sudo, just as you can create new users with almost no rights.
During the creation of the new user account it's a matter of defining in which groups the new user is gonna be.

---

### Post by Yellow Pasque on 2009-01-20
> Is it only the first account created during the installation which can use the sudo command?
No. The file /etc/sudoers determines who gets what privileges with 'sudo'. By default, the root user and anyone in the "admin" group can use sudo. To add a user to the admin group so that /he/she/it can use sudo:
```
sudo adduser <account_name> admin
```
(Obviously, you must execute this command as a user that's already priviledged)

NOTE: **DO NOT** edit /etc/sudoers directly unless you know what you're doing. If you must, use the 'visudo' command (and make sure you know enough about vi to edit and save a file).

---

### Post by sim085 on 2009-01-21
> **hyper_ch said:**
> for each user normally also an own group will be created.

Thanks,

I guess I will re-install the ubuntu server edition and set the first name of the username as 'administrator' since I feel this would reflect more my plans for this installation.

I do have other questions but I guess I will ask them as I go along :) Thank to everyone for all the help :) 

Regards,
Sim085

---

### Post by hyper_ch on 2009-01-21
that's not advised to do.

---

