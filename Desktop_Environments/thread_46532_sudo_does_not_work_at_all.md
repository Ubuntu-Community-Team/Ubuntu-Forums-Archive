---
title: "sudo does not work at all"
date: 2005-07-05
forum: Desktop Environments
---

### Post by ItIsMe on 2005-07-05
Whenever I enter a sudo command into terminal it does not work and says;



sudo: unable to lookup <username> via gethostbyname()
Password: postdrop: warning: unable to look up public/pickup: No such file or directory



I don't know if this is related but whenever I try to run anything under Administration under the System toolbar it will not run it. Because of this I can't set up any internet connections, printers or even open synaptic, which won't even open using Add/Remove Programs in Applications.

Most commands I have seen use sudo and I can't get any of them to work.

It think this thread goes under this category, not installation.

---

### Post by GrumpySimon on 2005-07-05
As far as I know, this is a result of a badly configured network setup. You should be able to fix it by editing /etc/hosts, and putting this line in it (or editing it if it's already there):

```

127.0.0.1       localhost.localdomain   localhost       COMPUTER

```

Where "COMPUTER" is the name you've given your computer - it'll be your terminal prompt.

--Simon

---

### Post by codejunkie on 2005-07-05
[QUOTE=ItIsMe]Whenever I enter a sudo command into terminal it does not work and says;



sudo: unable to lookup <username> via gethostbyname()
Password: postdrop: warning: unable to look up public/pickup: No such file or directory



I don't know if this is related but whenever I try to run anything under Administration under the System toolbar it will not run it. Because of this I can't set up any internet connections, printers or even open synaptic, which won't even open using Add/Remove Programs in Applications.

Most commands I have seen use sudo and I can't get any of them to work.

It think this thread goes under this category, not installation.[/QUOTE]

i have seen issues with sudo not working when you do a custom install and enable the shadow passwords option or some on has been playing with the sudoers file if you can't access any admin tasks such as add users etc with sudo did you ever enable the root password. if not you can enable it by rebooting the computer and choosing the (recovery mode) this will give you temp root privileges,  and enable the root user by typing
```

passwd root

```
and the new Root password this way you can at least have root privileges with the old su,gksu, and if your using kde/kubuntu kdesu commands. so you can at least get root access until you get it fixed.

---

### Post by ItIsMe on 2005-07-06
[QUOTE=GrumpySimon]As far as I know, this is a result of a badly configured network setup. You should be able to fix it by editing /etc/hosts, and putting this line in it (or editing it if it's already there):

```

127.0.0.1       localhost.localdomain   localhost       COMPUTER

```

Where "COMPUTER" is the name you've given your computer - it'll be your terminal prompt.

--Simon[/QUOTE]

I think that this may be the problem because when I log on a message comes up and says there may be a problem with the same file, /etc.hosts

And when I opened the file the line said;

```

127.0.0.1       localhost

```

When I tried to edit it I didn't have permission to do so, so I couldn't change it. Does anyone know how to fix this?

---

### Post by Morimando on 2005-07-06
login as root to fix this problem ^^

---

### Post by Lord Illidan on 2005-07-06
I think you have to add yourself to group wheel...

---

### Post by ItIsMe on 2005-07-06
[QUOTE=codejunkie]i have seen issues with sudo not working when you do a custom install and enable the shadow passwords option or some on has been playing with the sudoers file if you can't access any admin tasks such as add users etc with sudo did you ever enable the root password. if not you can enable it by rebooting the computer and choosing the (recovery mode) this will give you temp root privileges,  and enable the root user by typing
```

passwd root

```
and the new Root password this way you can at least have root privileges with the old su,gksu, and if your using kde/kubuntu kdesu commands. so you can at least get root access until you get it fixed.[/QUOTE]

Which session type is recovery mode? The menu had some different selections such as GNOME, failsafe and failsafe terminal. Which one do I use?

---

### Post by ItIsMe on 2005-07-06
[QUOTE=Morimando]login as root to fix this problem ^^[/QUOTE]

I am new to Ubuntu. How do you log in as root?

---

### Post by Morimando on 2005-07-06
The above post described it for you :) (the post from codejunkie)
In a terminal or console type 'passwd root' and give root a password, then you can login by typing 'su' in the terminal/CLI. Well, at least that's how it should work ;)

---

### Post by codejunkie on 2005-07-06
[QUOTE=ItIsMe]I am new to Ubuntu. How do you log in as root?[/QUOTE]
when you startup or reboot your computer you see the grub menu where you choose windows or ubuntu or ubuntu-(recovery mode)  you will see the choice that says (recovery mode) choose this it will log you in as root temporaily into the terminal-no gui here you can enable the root user with the command ```
passwd root
```
then enter the new password for the root user reboot the computer and login like normal now to gain root privliges under you user account  open a terminal and type the command su then hit enter, enter password you just set and now to open app as root just type the name of the app like synaptic this will open synaptic hope this helps.

---

### Post by frodon on 2005-07-06
[QUOTE=Morimando]then you can login by typing 'su' in the terminal/CLI.[/QUOTE]
Be careful, in ubuntu you must use "sudo su" command to get root, only "su" will not work, newbies don't always know that.

---

### Post by codejunkie on 2005-07-06
[QUOTE=frodon]Be careful, in ubuntu you must use "sudo su" command to get root, only "su" will not work, newbies don't always know that.[/QUOTE]
the person that started the thread said they have no sudo privileges so they can't use sudo they will have to use su by enabling the root account first so they can add themself to the sudoers file. but this is a good point first because to gain root access by using sudo they can't just open a terminal and type ```
sudo
```it has to be ```
sudo su
``` or ```
sudo -s
``` so this question is to > **ItIsMe** have you tried to gain root access by opening a terminal and typing ```
sudo su
``` or did someone just tell you to gain root access in ubuntu you just have to use just > sudo if so you might want to try sudo su before you go through trouble of enable the root account.

---

### Post by ItIsMe on 2005-07-06
I've tried using

*sudo su* 

but that doesn't work either. But I can use the *su* command in terminal. Is there some way to edit the */etc/hosts* file using this to make it look like
```

127.0.0.1       localhost.localdomain   localhost       COMPUTER

```
And will this help solve the problem?

---

### Post by codejunkie on 2005-07-06
[QUOTE=ItIsMe]I've tried using

*sudo su* 

but that doesn't work either. But I can use the *su* command in terminal. Is there some way to edit the */etc/hosts* file using this to make it look like
```

127.0.0.1       localhost.localdomain   localhost       COMPUTER

```
And will this help solve the problem?[/QUOTE]
switch to root with su and type gedit /etc/hosts

---

### Post by ItIsMe on 2005-07-06
[QUOTE=codejunkie]switch to root with su and type gedit /etc/hosts[/QUOTE]

I used *su* and changed the file, as well as adding myself into the sudoers file, and now all the sudo commands work! 
Thanks for the help.
One last thing, now when I open something under administration, under the System toolbar, it asks for a password. What do I type in, as niether my password or root's password have worked.

---

### Post by codejunkie on 2005-07-06
[QUOTE=ItIsMe]I used *su* and changed the file and now all the sudo commands work! 
Thanks for the help.
One last thing, now when I open something under administration, under the System toolbar, it asks for a password. What do I type in, my password, or root's password?[/QUOTE]
your password
now that you have sudo working again you might want to think about turning off the root acount with ```
sudo passwd -l root
``` this is just to make your system a little more secure you know but its up to you if you feel comfortable using both.

*Well now that i have just seen your edit neither work on there the first thing to check here is the user manager with this command as root ```
users-admin
```click on you username then properties then under user privliges make sure the box Executing system administration tasks is checked if it is and you still don't have sudo privliges you have to add your user account to the sudoers file here is a guide that describes how to do that [http://ubuntuguide.org/#allowmoresudoers](http://ubuntuguide.org/#allowmoresudoers) hope this helps.*

---

### Post by ItIsMe on 2005-07-06
Thanks for the help.

It runs perfectely now.
 :)   :)

---

