---
title: "Issue with several admin programs"
date: 2006-09-28
forum: Desktop Environments
---

### Post by disk11 on 2006-09-28
If I try to run Synaptic, Update Manager, or Users and Groups via the Gnome menus, nothing pops up.  Sometimes I get a window on the bottom panel that says loading whatever app I'm trying to open.  These 3 programs run fine via the terminal however.  I'm guessing a GNOME bug since I tried booting an older kernel I have loaded and the issue persisted.

---

### Post by amohanty on 2006-09-28
Try reinstalling gksu:
**sudo apt-get install gksu**
 
and try again. If that doesnt work, open a terminal and type in:
**gksudo -S -d synaptic**

And post the output.

HTH
AM

---

### Post by disk11 on 2006-09-28
```
matt@Ubuntu:~$ gksudo -S -d synaptic
xauth: /tmp/libgksu1.2-0OBd5N/.Xauthority
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: synaptic
buffer: -Xlib: connection-
No password prompt found; we'll assume we don't need a password.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:7065): Gtk-WARNING **: cannot open display:
xauth: /tmp/libgksu1.2-0OBd5N/.Xauthority
xauth_env: /home/matt/.Xauthority
dir: /tmp/libgksu1.2-0OBd5N

```

---

### Post by disk11 on 2006-09-28
I fixed it with
```
xhost +LOCAL:
```

---

### Post by drpaul on 2006-09-28
That's not the default. You're disabling some kind of protection. I have the same trouble with Firestarter and reset xhost back to - after starting.

It would be nice to understand why that happens and how to properly avoid it.

Paul

---

### Post by amohanty on 2006-09-28
> **disk11 said:**
> I fixed it with
```
xhost +LOCAL:
```

You probably dont want to do that.
Can you post the output of:
**ls -al ~/.X***
**ls -al ~/.ICE***
and
**ls -al /root**

---

### Post by disk11 on 2006-09-28
Why is what I did a bad idea?

Here's the output:
```
matt@Ubuntu:~$ ls -al ~/.X*
-rw------- 1 root root 169 2006-09-28 10:48 /home/matt/.Xauthority
matt@Ubuntu:~$ ls -al ~/.ICE*
-rw------- 1 matt matt 481 2006-09-28 15:35 /home/matt/.ICEauthority
matt@Ubuntu:~$ ls -al ~/.ICE*
-rw------- 1 matt matt 481 2006-09-28 15:35 /home/matt/.ICEauthority

```

---

### Post by amohanty on 2006-09-29
> Why is what I did a bad idea?

There are security issues associated with using xhost. I would suggest a quick read of [http://bau2.uibk.ac.at/matic/ccxsec.htm](http://bau2.uibk.ac.at/matic/ccxsec.htm) before you use it.

> matt@Ubuntu:~$ ls -al ~/.X*
-rw------- 1 **root** **root **169 2006-09-28 10:48 /home/matt/.Xauthority

This is the root (no pun intended) of your problem. Try the following:

**sudo chwon matt:matt /home/matt/.Xauthority**

and try again.

HTH
AM

---

### Post by fragos on 2006-09-29
If you can't run administrative applications, check that the hostname and hosts file have your hostname.  In my case, my hostname is Geo so therefore:

/etc/hostname must be "Geo"
/etc/hosts must start with "127.0.0.1 localhost Geo"

---

### Post by disk11 on 2006-09-29
> **amohanty said:**
> There are security issues associated with using xhost. I would suggest a quick read of [http://bau2.uibk.ac.at/matic/ccxsec.htm](http://bau2.uibk.ac.at/matic/ccxsec.htm) before you use it.



This is the root (no pun intended) of your problem. Try the following:

**sudo chwon matt:matt /home/matt/.Xauthority**

and try again.

HTH
AM

I can now run Synaptic and Update-Manager when I run them via the terminal, but they still don't work via the Gnome menu.

@ fragos: I just checked and both of those files are setup correctly.

---

### Post by amohanty on 2006-10-01
> I can now run Synaptic and Update-Manager when I run them via the terminal, but they still don't work via the Gnome menu.

How are you running them from a terminal?

Also could you post the contents of your /etc./sudoers?


AM

---

### Post by Topper_H on 2006-10-01
I got rid of the same problem by cleaning up my /etc/sudoers

Hope it helps

---

### Post by disk11 on 2006-10-01
> **amohanty said:**
> How are you running them from a terminal?

Also could you post the contents of your /etc./sudoers?


AM

"sudo synaptic" runs fine, gksudo gives me this:
```
matt@Ubuntu:~$ gksudo synaptic
Xlib: No protocol specified


(synaptic:6085): Gtk-WARNING **: cannot open display:

```

The only change I have made to sudoers is letting Firestarter start w/o the admin password
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
matt ALL=NOPASSWD: /usr/sbin/firestarter
```

---

### Post by amohanty on 2006-10-01
Why are you doing this:
> env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

and try again.
if that doesnt help try **gksudo -l synaptic**

The problem still is that one of your .Xauth files has crapped out. If that doesnt work either, delete your .Xauthority and .ICEauthority files and reboot.

HTH
AM

---

### Post by disk11 on 2006-10-01
I dunno where that stuff came from.  But deleting it fixed gksudo.  Thanks for the help everyone.

---

### Post by Srirangan on 2006-10-03
I have the same problem, how do I fix it?

Apparently I can't delete the subdoers because "don't have sufficient rights"!

---

### Post by disk11 on 2006-10-03
> **Srirangan said:**
> I have the same problem, how do I fix it?

Apparently I can't delete the subdoers because "don't have sufficient rights"!

You don't want to delete sudoers, that could cause a really big problem.

> **SqRt7744 said:**
> 
Now edit /etc/sudoers (after backing it up as /etc/sudoers.bak).  The file claims that it should only be edited with "visudo".  I'm skeptical, but whoever wrote that in the file presumably had a good reason to do so.  To be safe I will follow advice and use visudo here:

```

sudo cp /etc/sudoers /etc/sudoers.bak
export VISUAL="vim"
sudo visudo

```



Pulled from [http://ubuntuforums.org/newreply.php?do=newreply&p=1024069](http://ubuntuforums.org/newreply.php?do=newreply&p=1024069)

---

### Post by Srirangan on 2006-10-04
Can't edit - Not Enough Permissions!

I'm screwed :(

---

### Post by disk11 on 2006-10-04
Maybe figure out how to log in as the root user from the initial login screen?  Or have you tried any of this stuff as root?

---

### Post by bapoumba on 2006-10-04
@ Srirangan : from  grub, choose the recovery mode. Carefull, you'll be root.
Then
```
cat /etc/sudoers
```
and make sure the bottom of your sudoers file looks like :
```
# Defaults

Defaults	!lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

and that you are in the adm and admin groups (type groups to verify)
You can fix your sudoers file from the recovery mode.

---

