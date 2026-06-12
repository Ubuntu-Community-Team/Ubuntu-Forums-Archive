---
title: "using SUDO"
date: 2005-11-12
forum: Desktop Environments
---

### Post by drakulaj on 2005-11-12
heloo im totally lama. I have this problem after my first run kubuntu i can access all sith command SUDO anh giving my user password. After my first reboot it is not akcepting my password in SUDO or anywhere else. Whats Wrong?

Jirka

---

### Post by raublekick on 2005-11-12
hmm... not quite sure what your problem is in particular, but i'll try to help.

here is a basic run-down of using sudo:
you use sudo when you need to run a command that requires root access. you can usally tell if you run a command without sudo and it gives you problems.

to use sudo, just add it to the front of the command, like so:
```
sudo apt-get install somepackage
```

it will ask for your password before it runs the command. enter it, but be aware that no characters appear on the screen. your password is being entered as you type, however.

just press enter and it should work.


the sudo password should be the same as your user password if you are the one who installed Kubuntu

---

### Post by drakulaj on 2005-11-12
no its not working, its absolutely not akcepting my passwrod. Its asked my for password, i type it, hit enter and nothings happend. Maybe BUG??

---

### Post by bluemuffin on 2005-11-17
[QUOTE=drakulaj]heloo im totally lama. I have this problem after my first run kubuntu i can access all sith command SUDO anh giving my user password. After my first reboot it is not akcepting my password in SUDO or anywhere else. Whats Wrong?

Jirka[/QUOTE]

Please don't interpret this as being rude but is there any chance that you mayhave forgotten your password?

There are 12 of us using breezy right this moment and we are not having problems using our root and user passwords (we are new to ubuntu too and are sharpening our skils). So there is a chance that what you are experiencing is not a bug.

I'm not sure, but it seems that you may need to re-install ubuntu if you forget the password.

regards.

---

### Post by Miguel on 2005-11-17
There is no need to reinstall ubuntu. If you have physical access to the computer, you can gain root access from grub during boot time. Entering as root will allow you to:
[list][*] Change your user's password without knowing the old one
[*] See if you are still in the sudoers group
[/list]

But first, a question: Do you really remember your password? I mean, you are asked your username and password everytime you login. If you can login, you should know your password... unless you configured GDM not to ask your password (unsafe!!).

---

### Post by Haegin on 2005-11-17
Have you tried running ```
sudo passwd
``` from a terminal - it will ask you for your password (try it anyway) and then allow you to set a new one. I think I had to do it when I installed as I had a similar problem.

Hope this helps

---

### Post by the_it on 2005-11-17
sudo is automatically enabled for the FIRST USER created in the Ubuntu installer.  If you created additional users in the installer, they do not by default have sudo access.

Just to make sure we cover all bases.

---

