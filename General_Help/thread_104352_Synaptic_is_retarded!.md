---
title: "Synaptic is retarded!"
date: 2005-12-15
forum: General Help
---

### Post by bslusser on 2005-12-15
so I finally have ubuntu installed and im ready to install some programs, so i click on the synaptic package manager it asks for my password i type it in, and nothing. Nothing launches or anything. neither does applications->add application. and yes I am typing the right password in.does anyone have any ideas?'

I also notice that the other administrative programs do not launch also such as disks and users and groups.

---

### Post by soulestream on 2005-12-15
open a terminal type

passwd

and change your password. if no apps are working under sudo, then something is wrong with your password probably

soule

---

### Post by aysiu on 2005-12-15
Go to Applications > Accessories > Terminal
Type in ```
gksudo synaptic
``` What happens? Can you post the terminal output?

---

### Post by 23meg on 2005-12-15
Post the contents of your /etc/hosts file.

---

### Post by bslusser on 2005-12-15
changing my password does not work. the administartive programs dont even ask for it now. nothing launches. :(

---

### Post by bslusser on 2005-12-15
blake@BigBlu:~$ gksudo synaptic

this did nothing and outputted nothing. weird huh?


blake@BigBlu:~$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost       BigBlu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
blake@BigBlu:~$

---

### Post by aysiu on 2005-12-15
Let's separate out the issues:
1. Password
2. Launching of graphical apps

Okay. To isolate the password issue, try this: ```
sudo apt-get update
``` When prompted for your password, enter the password of the first user you created during installation.

---

### Post by aysiu on 2005-12-15
[QUOTE=bslusser]blake@BigBlu:~$ gksudo synaptic

this did nothing and outputted nothing. weird huh?[/QUOTE] Yes, that is weird. I attached a screenshot of what *should* have happened.

---

### Post by bslusser on 2005-12-15
sudo apt-get update does nothing. my password is correct because thats what i use to login with. ive tried restarting but nothing happens. is sudo messed up or something?

---

### Post by bslusser on 2005-12-15
anything that requires sudo does not work. sudo doesnt even ask for passwords it just doesnt go through. what are the commands to reinstall sudo? mabey i can reinstall from root.

---

### Post by RobertLos on 2005-12-16
Got some problems myself but only with gksudo. sudo does work. Try from a terminal the following:

cat /etc/group | grep yourloginname

my login name is robert so the command lists the following:
robert@max:~:501 % cat /etc/group | grep robert

adm:x:4:robert
dialout:x:20:robert,cupsys
cdrom:x:24:robert,hal
floppy:x:25:robert,hal
audio:x:29:robert
dip:x:30:robert
video:x:44:robert
plugdev:x:46:robert,hal
robert:x:1000:
lpadmin:x:107:robert
scanner:x:108:robert
admin:x:109:robert
robert@max:~:502 %

As you can see i am a member of the admin group. This is essential. You must also be a member of admin. If not try following

sudo passwd

enter a password of your choice.
You can than become root by

% su
the prompt changes to #
add your account to the admin group with e.g. gedit /etc/group or vi /etc/group

does this help?

---

### Post by bslusser on 2005-12-16
hmm lemme fiddle with this...


Okay where you have admin: x:109:robert, I dont have an admin line anywhere in the /etc/group  how do i add this?

---

### Post by bslusser on 2005-12-16
nevermind i fixed it. found out my group wasnt added to the sudoers list.

---

### Post by Kevinator on 2005-12-17
By default, only the user you create during system installation is a member of the admin group, and only members of that group can use sudo. If you created a new account for yourself after installation, that is probably why it did not work - it wasn't a member of the admin group.

Once you use sudo and provide a password, it remembers you for a while (15 minutes, I think), so you don't have to enter a password every time. This may be why you weren't even getting prompted sometimes.

---

### Post by angrykeyboarder on 2005-12-17
[QUOTE=Kevinator]By default, only the user you create during system installation is a member of the admin group, and only members of that group can use sudo. If you created a new account for yourself after installation, that is probably why it did not work - it wasn't a member of the admin group.

Once you use sudo and provide a password, it remembers you for a while (15 minutes, I think), so you don't have to enter a password every time. This may be why you weren't even getting prompted sometimes.[/QUOTE]

However.....

Type "expert" at the install prompt instead of "install" and that changes everything.....

(Including giving you the ability to establish a root password).

Also, I typed my name wrong when I created my normal user account. Not realizing that at the time, I created another user account with the correct spelling.  That account wasn't in the admin group.

I figured that out after a while and fixed it.  I never did figure out if the account I created with the misspelled name 
had admin privileges though. I deleted it without checking. lol

---

