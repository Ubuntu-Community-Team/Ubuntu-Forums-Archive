---
title: "Sudo access rights"
date: 2010-11-11
forum: Desktop Environments
---

### Post by 1opstrader1 on 2010-11-11
HI,
 New LInux user here :)
 I just added my ubuntu 10.10 to an AD domain. Per my rights in AD I am a domain admin.
Now when I try to run anything under my AD login, I keep getting a message about not having rights or am I root.
 This is even happening when I login with my local linux accout before adding this machine to AD. I was not having this
problem before.
 I have checked my rights and have even ran the sudo visudo and added  my local login account and domain AD account. I was not sure if that  would even help, but did it anyway.
 I have had to enable the root login account (I know bad idea) to get anything done on the system.
Is there a way to add the domain account to sudo users group?
 Everytime I try to run anything it tells me I am not in the (sudoers)  group. Also even when I sudo + command it tells me I am once again not  in the (sudoers) group.
 Thanks - Ron

---

### Post by Crusty Old Fart on 2010-11-11
There might be several reasons for what is happening.

However, since the system is informing you that you are not in the sudoers group, it might help to add the users you want to this group.

Assuming a user name: **username**

From a shell, as root:
```

usermod -G sudoers **username**

```

By the way, and this question might be coming a little late, but what is: AD?

Good Luck!

---

### Post by cmcx_linux on 2010-11-11
Linux workstation integrates into a windows active directory (AD) only when it comes to samba ( files & printers). The samba users ( domain users) may or may not overlap with the local unix users. Another note, in the windows AD you can have one or more domain admins which can reign over the enterprise's infrastructure. This is not true with an unix. In linux you only have one Admin which is root who can be God of the system. Samba won't ever overlap by itself something to root, and it's not even recommended. 
So, to conclude, 
1. you need to have samba installed and/or ldap ( never used it). 
2. you need to edit the samba's users ( each desktop flavour usually has a nifty tool to edit samba users) to allow your domain users to access shares on the linux workstation.
3. you need to edit your samba shares, and optionally setup user access.

If you need remote login and console rights a la AD, forget it. It won't work. Enable remote desktop on your gnome or use x11vnc on your kde, and also it's good to have a ssh server up and running.  Install putty on your domain server and a vnc client to be able to access and rdp your linux workstation.
USE YOUR REGULAR LINUX USER ACCOUNT TO LOG IN. THE ONE YOU SETUP WHEN YOU INSTALLED THE SYSTEM. FORGET ABOUT THE AD for now. By default linux/mac/unixes don't give 2 cents on domain logins because they weren't meant to work that way. Try to install [http://www.likewiseopen.org/](http://www.likewiseopen.org/), you'll find it on terminal sudo apt-get install likewise-open and add the station to the domain using that tool. Hope it helps you.

---

### Post by 1opstrader1 on 2010-11-11
Being new to linux, i should have known better to think that AD rights would reside on a linux box.
I had in the back of my mind that samba was needed, but I wanted confirmation on that point.

I actually did use likewise open to add it to the AD domain and I was actually surprised that it worked
because I had done some research on it and some users were having tons of DNS or LDAP issues.

I will proceed with the samba option and thanks for the advice and confirmation.

---

