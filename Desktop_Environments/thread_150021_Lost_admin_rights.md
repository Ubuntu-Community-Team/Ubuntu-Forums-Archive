---
title: "Lost admin rights"
date: 2006-03-25
forum: Desktop Environments
---

### Post by QOLIM on 2006-03-25
I think I somehow lost admin rights
because i cant open things like firestarter, root terminal, user groups etc...
but i can still open firefox, terminal (but cant be root)
And it is the only account on this computer.
I think I lost permissions to '/' 
o is there any way to be admin again and be able to do anything?

Thx

---

### Post by codejunkie on 2006-03-25
[QUOTE=QOLIM]I think I somehow lost admin rights
because i cant open things like firestarter, root terminal, user groups etc...
but i can still open firefox, terminal (but cant be root)
And it is the only account on this computer.
I think I lost permissions to '/' 
o is there any way to be admin again and be able to do anything?

Thx[/QUOTE]
open a terminal and enter ```
sudo su
```this should give you root access, if that doesn't work reboot at the grub menu choose (recovery mode). when you reach the terminal enter ```
sudo passwd root
```and set the password for the root account reboot by entering ```
reboot
```and login as your normaly would, then open a terminal and enter ```
su
```enter the password you just set and run ```
users-admin
```this should let you changes permissions add users and such, make sure your username is in the admin group if it is not add it to the admin group and sudo should work again.

---

### Post by QOLIM on 2006-03-25
already tried that, but no succes :(

if i use 'su' it says: > Authentication failure

And if i use a command with sudo like 'sudo passwad root'
it says > Must be setuid root

---

### Post by Mustard on 2006-03-25
Use the 'Recovery Mode from the Grub menu at startup.

Recovery mode will drop you to a root prompt.  If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..

```
visudo  #this command does on thing.  It opens the sudoers file for editing
```

My sudoers file looks like this.  Note the last line where I give my user sudo privileges.  This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

You can see my username on the bottom line.  You would need to add your username to the bottom as I have done.

Assuming your user name was "bob'', then the line that would need to be added would be..
```
bob ALL=(ALL) ALL
```

This is just one way of doing it.  Some sudoers files are set up with an admin group called 'adm'.  Users are then added to the adm group, and a line in the sudoers file that looks like this below gives members of the 'adm' group admin access.
```
%adm ALL=(ALL) ALL
```

If you decided to do it this way you would create the line above at the bottom of your sudoers file then do this command (substituting your username in the appropriate place)..

```
adduser your_username adm
```

---

### Post by QOLIM on 2006-03-25
When i try visudo:> visudo: /etc/sudoers:Permission denied

And when I try> gedit /etc/sudoers It opens but I cant add or edit anything

---

### Post by Mustard on 2006-03-25
[QUOTE=QOLIM]When i try visudo:

And when I try It opens but I cant add or edit anything[/QUOTE]

Are you booting up in recovery mode from the grub menu?

---

### Post by Smakfull on 2006-03-25
everythings ok now! Su worked though I don't know why. Thanks anyway.

---

### Post by Smakfull on 2006-03-25
[QUOTE=Smakfull]I've got the same problem. I did all of the above, including editing and saving the file of course, but nothing happens. I know that I have changed ownership on /var/run/sudo accidently by chmod but putting myself in the sudoers-file doesn't do a thing. Am I still doing something wrong? I have entered the recovery mode correctly.[/QUOTE]
I guess I'm fumbling with saving but I can't guess how :-k

---

### Post by BLTicklemonster on 2006-09-05
I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

### Post by xykaum on 2008-04-27
Hello!

I had the same problem and I tried the steps listed above but I still can't run the sudo command without the following return:

```

xykaum@preto:~$ sudo su
sudo: unable to resolve host preto

```

When I tried using the recovery mode by editing the sudoers file:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
xykaum ALL=(ALL) ALL


```

It didn't resolved the problem. So I tried the commands in recovery mode:
```

sudo passwd root

```

It returned the same error:
```

root@preto:~# sudo su
sudo: unable to resolve host preto

```

So I tried :

```

#passwd root
#reboot

```

And su is working again, but still nothing about sudo.

I used the tip of BLTicklemonster as root:
```

root@preto:/home/xykaum# ls -l /usr/bin/sudo
-rwsr-xr-x 2 root root 107776 2008-02-25 08:22 /usr/bin/sudo

root@preto:/home/xykaum# chown root:root /usr/bin/sudo

root@preto:/home/xykaum# chmod 4755 /usr/bin/sudo


```

But sudo still don't works.

Someone have any idea wht should I do to fix this problem?

---

