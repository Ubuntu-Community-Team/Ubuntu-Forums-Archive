---
title: "need help with my su password"
date: 2005-06-07
forum: Desktop Environments
---

### Post by Olflo on 2005-06-07
hi there,
i think i need some help. my problem is: I can use my password for all kinds of purposes  including sudo, but the system wont accept it with the command su and i cannot access the administrator mode in the Kubuntu Control Center with it. I urgently need to do a few things in there, but I cannot access it. I always thought the administrator password is identical with my usual password and i do not remember having declared any other password during install.

---

### Post by Arthemys on 2005-06-07
In Ubuntu there is no root password, therefor no password for su. If you need a root prompt type in 'sudo -s -H' and that will put you into a root shell until you exit it. Hope that helps some.

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=Olflo]hi there,
i think i need some help. my problem is: I can use my password for all kinds of purposes  including sudo, but the system wont accept it with the command su and i cannot access the administrator mode in the Kubuntu Control Center with it. I urgently need to do a few things in there, but I cannot access it. I always thought the administrator password is identical with my usual password and i do not remember having declared any other password during install.[/QUOTE]
 try sudo kcontrol

---

### Post by MBMESSAOUD on 2005-06-08
I have the same problem
when I type  ```
sudo -s -H
``` I get a prompt for password

```
 sudo -s -H
Password:
```

---

### Post by kvidell on 2005-06-08
[QUOTE=MBMESSAOUD]I have the same problem
when I type  ```
sudo -s -H
``` I get a prompt for password

```
 sudo -s -H
Password:
```[/QUOTE]
 it wants your user password.

---

### Post by MBMESSAOUD on 2005-06-08
When I give my user password 
I get this message

```
 sudo -s -H
Password:
mokhtar is not in the sudoers file.  This incident will be reported.

```

How to add my username in sudoers file ?

---

### Post by Peter Alien on 2005-06-08
[QUOTE=Arthemys]In Ubuntu there is no root password, therefor no password for su. If you need a root prompt type in 'sudo -s -H' and that will put you into a root shell until you exit it. Hope that helps some.[/QUOTE]

How can that be ?!!!! 

Before i install Ubuntu i read the same thing, but when i installed it i made some changes in Ubuntu, and now i have a Root user with his own pass and i have a user (me) with my own password.

When i type SU in Konsole i put the root password, and when i use SUDO i enter my own password.

I just don't remember how i activated the Root  :???: damn 

But for now my Ubuntu works like this :)

e.g.

In Konsole:

pedro@Unreal:~$ su
Password: ***** <- Root password
root@Unreal:/home/pedro #


 :grin:

---

### Post by Joeb on 2005-06-08
[QUOTE=Peter Alien]How can that be ?!!!! 

Before i install Ubuntu i read the same thing, but when i installed it i made some changes in Ubuntu, and now i have a Root user with his own pass and i have a user (me) with my own password.

When i type SU in Konsole i put the root password, and when i use SUDO i enter my own password.

I just don't remember how i activated the Root  :???: damn 



 :grin:[/QUOTE]


You probably created a root user and assigned a password to it.  Without getting into the argument about "su" vs "sudo" (it's like arguing religion or what gnome vs kde), you probably should choose one or the other and not both (ie disable one of them) for your system maintenance chores.  As for me, it took me a long time to get used to not having a root user, but to tell you the truth, I haven't found one thing I can't do without it.

---

### Post by MBMESSAOUD on 2005-06-08
I can connect to root using 
```
mokhtar@syspc128:~/Desktop$ su
Password:
root@syspc128:/home/mokhtar/Desktop #
```

but using **sudo** with the same password as **su** I get this error

```
mokhtar@syspc128:~/Desktop$ sudo -s -H
Password:
Sorry, try again.
Password:

```


I have also error when using **System/Administration/Synaptic Package Manager** and after typing the same password as used with **su**
Failed to run /usr/sbin/synaptic:
 Wrong password.

Could you please tell me what I missed in ubuntu configuration ?!!

---

### Post by sbassett on 2005-06-08
[QUOTE=MBMESSAOUD]I can connect to root using 
```
mokhtar@syspc128:~/Desktop$ su
Password:
root@syspc128:/home/mokhtar/Desktop #
```

but using **sudo** with the same password as **su** I get this error

```
mokhtar@syspc128:~/Desktop$ sudo -s -H
Password:
Sorry, try again.
Password:

```


I have also error when using **System/Administration/Synaptic Package Manager** and after typing the same password as used with **su**
Failed to run /usr/sbin/synaptic:
 Wrong password.

Could you please tell me what I missed in ubuntu configuration ?!![/QUOTE]


When you perform sudo, this will ask for your user password, not the root password. Root's password is null by default.  But this does not mean that it does not require a password. In effect the root account is unusable.


If you have your system setup so root has a password, su or su - will ask for the root password, not your user password.

I hope this helps, and didn't confuse even further with my explanation methods.

---

### Post by MBMESSAOUD on 2005-06-09
Ok 
Now It is fine

I jave edited sudoers with **visudo** and added the line
```
mokhtar ALL=(ALL) ALL
```

so now using my username **mokhtar** I can run synaptic from gnome menu

Thanks for help

---

### Post by Olflo on 2005-06-09
Hello everyone,
I'm impressed by the discussion I started off. Seems I'm not the only one with problems in that area.
All your postings have helped me insofar as:
1) I now understand there is no separate root account. Noone is listed as superuser, that' s why su won't work. I don't need su, I can use sudo for single commands or a root console for a longer session (accessible thru sudo -s -H or the K Menu, there is an Entry Root terminal there.)
2) typing sudo kcontrol brings up a bunch of error messages:

Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kcontrol, it probably crashed.
olflo@ubuntu:~$ Error: "/tmp/ksocket-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"

but finally launches an instance of Control Center that is owned by root. Here, various options are accessible that are missing when I start Control Center from the K Menu. There is a button offering Administrator Mode on the relevant pages, pushing it brings up a dialogue asking for my password, but I enter it to no effect other than kcontrol showing its start screen. There seems to be a problem here in the way the password is used internally. Kcontrol and Ubuntu do not work together properly here. I will post this at the Kubuntu Forum for some developers to worry about.

3) My only question remaining is: How can I get the K Menu entry for Control Center to automatically start an instance of Kcontrol owned by root instead by me as a user? Ifg anyone knows na workaround, i will be happy.

---

### Post by zAo on 2005-06-09
try 
```
kdesu kcontrol
```

---

