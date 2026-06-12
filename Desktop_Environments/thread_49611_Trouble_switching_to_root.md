---
title: "Trouble switching to root"
date: 2005-07-17
forum: Desktop Environments
---

### Post by JoeS on 2005-07-17
I would like help in enabling Root. I typed      ```
sudo passwd root
```
I entered my user password.  Then typed the new unix password and confimed.

I tried using the Add/Remove programs, and the Synaptic Package Manager, but it wouldn't accept the new password I entered for Root. It still wants my user password. 

Why am I not switching from Sudo to Root?

---

### Post by not_yet on 2005-07-17
> Why am I not switching from Sudo to Root?

sudo is root

for example to use gedit as root I would enter

sudo gedit

it will then ask you for the  password

---

### Post by codejunkie on 2005-07-17
because when you enable the root with ```
sudo passwd root
``` it does not change the commands to launch the applications in the menu it only enables the root account. if you want apps in the menu like synaptic for example to ask for the root password instead of your password, you have to manually edit it's .desktop file. 
the reason it's not working is because the command in the System/Administration menu to launch synaptic is ```
gksudo /usr/sbin/synaptic
``` this will ask for your password, to make it ask for the root password you have to change it to ```
gksu /usr/sbin/synaptic
``` this will make it do what you want it to but it might take some time hunting down and editing those .desktop files hope this helps.

---

### Post by JoeS on 2005-07-17
When I used the command:
```
sudo passwd root
```
I must have done something wrong. I can't log in as root.

When I typed the command I was asked for my password.  I typed in my user password  ;  when it asked for my new unix password I typed in the password I wanted to use for root and cofirmed.  I then received the message:  Password updated successfully
 Am I understanding this correctly?  What is wrong?

I then tried to log in as root with the new unix password and couldn't.

---

### Post by codejunkie on 2005-07-17
when you enabled the root password you cant login as root at the login screen right, you have to enable that by going to System/Administration/Login Screen Setup click on the security tab  and put a check in the box Allow root to login with GDM hope this helps.

---

### Post by JoeS on 2005-07-25
Is there a way to turn Sudo off.  I don't see the point in having 2 accounts to log into root: With the root acccount enabled  I can log into root directly and also through Sudo.

---

### Post by JoeS on 2005-08-25
[QUOTE=codejunkie]if you want apps in the menu like synaptic for example to ask for the root password instead of your password, you have to manually edit it's .desktop file.
the reason it's not working is because the command in the System/Administration menu to launch synaptic is
Code:

gksudo /usr/sbin/synaptic

this will ask for your password, to make it ask for the root password you have to change it to
Code:

gksu /usr/sbin/synaptic

this will make it do what you want it to but it might take some time hunting down and editing those .desktop files hope this helps.[/QUOTE]


I found 2 files:
[INDENT]synaptic.desktop  /etc/X11/sysconfig[/INDENT]
[INDENT]synaptic.desktop  /usr/share/control-center-2.0/capplets[/INDENT]

and edited them to:
[INDENT]Exec=gksu /usr/sbin/synaptic[/INDENT]

I still cannot access synaptic with the root password.  Any suggestions?

I also tried to open the synaptic and the update-manager through the terminal after switching to root and was denied.  Why is this?

Thanks for help.

---

