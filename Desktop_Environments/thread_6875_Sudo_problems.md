---
title: "Sudo problems"
date: 2004-12-02
forum: Desktop Environments
---

### Post by VaDor on 2004-12-02
Hy

I am having sudo problems.  I have the root acount enable but sometimes i need to use sudo. But i can't  here is the problem:

[B]vador@speedy:~ $ sudo gcc
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
sudo: 2 incorrect password attempts
vador@speedy:~ $[/B]

I type correctly the password but is reject. I know if i am not in the sudoers file this can happen but my sudoers file is like this:

# Defaults

Defaults        !lecture,tty_tickets

# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
vador   ALL=(ALL) ALL




Anyone knows what i have to do to sudo works?
thks  ;-)

---

### Post by bazuka on 2004-12-02
I am assuming you've already done "sudo passwd root" and set it. If not, do that first.

---

### Post by liberal_tugboat on 2004-12-02
[QUOTE=VaDor]Hy

I am having sudo problems.  I have the root acount enable but sometimes i need to use sudo. But i can't  here is the problem:

[B]vador@speedy:~ $ sudo gcc
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
sudo: 2 incorrect password attempts
vador@speedy:~ $[/B]

I type correctly the password but is reject. I know if i am not in the sudoers file this can happen but my sudoers file is like this:

# Defaults

Defaults        !lecture,tty_tickets

# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
vador   ALL=(ALL) ALL




Anyone knows what i have to do to sudo works?
thks  ;-)[/QUOTE]
 you have to put YOUR password in for sudo, even if you have the root account enabled

---

### Post by bob k on 2004-12-02
[QUOTE=liberal_tugboat]you have to put YOUR password in for sudo, even if you have the root account enabled[/QUOTE]
 You most probaly hit the caps lock key or something like it when entering the password. There is a password cracker in universe, I've never had to use it. I would start withe the keys around my password.

Bob

---

### Post by VaDor on 2004-12-03
[QUOTE=bazuka]I am assuming you've already done "sudo passwd root" and set it. If not, do that first.[/QUOTE]

Nop I choose in boot i think safe mode or something. The i enter in root , in there I did passwd , I reboot again enter in "normal" kernel , and i have root account when i do su i can enter in the account or if o login as root i can do it:

[B]root@speedy:~ # sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@speedy:~ #[/B]

Then i wen has user and do this but:

[B]vador@speedy:~ $ sudo gcc
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
sudo: 2 incorrect password attempts
vador@speedy:~ $[/B]


 =;  next i tried this yet again:

[B]vador@speedy:~/leic/trabalhos/proxyweb $ sudo passwd root
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
sudo: 2 incorrect password attempts
vador@speedy:~/leic/trabalhos/proxyweb $
[/B]


So i can't still use SUDO!!  I can use  su  and i can login as root in a shell but can't use  SUDO   :mad:

---

### Post by HungSquirrel on 2004-12-03
Just to be absolutely clear, when you enter the sudo command and you enter your password, are you entering the root password and getting errors, or are you entering your user account password?  Root's password will not work but your user account's is supposed to.

---

### Post by VaDor on 2004-12-03
[QUOTE=HungSquirrel]Just to be absolutely clear, when you enter the sudo command and you enter your password, are you entering the root password and getting errors, or are you entering your user account password?  Root's password will not work but your user account's is supposed to.[/QUOTE]

I was putting root password  #-o    erghh i was thinking that to change password in sudo i would need always root password......  #-o   now i put user password and i can use sudo   :D 


Thanks erghh  so simple and i couldn't see  :cry: 




Thanks everyone  now everything is working  =D>

---

### Post by cu_ on 2005-05-17
I am having the same issue...  did any of you find a solution?

I started having these problems after I installed the nx-server.  I don't know if this has to do with anything.

--cu

---

### Post by cu_ on 2005-05-17
[QUOTE=cu_]I am having the same issue...  did any of you find a solution?

I started having these problems after I installed the nx-server.  I don't know if this has to do with anything.

--cu[/QUOTE]
 Never mind... I found the solution for it.  You could do it one of many ways
1.  You can edit etc/sudoers file and inclue logins.  There is a man page that explains how to edit this file.
2. sudoers file by default allows everyone in the root group to become sudoers, so include yourself in the root group.
3.  There is a group called 'sudo' group. Include your login in that group.

---

