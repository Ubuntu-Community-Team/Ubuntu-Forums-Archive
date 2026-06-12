---
title: "sudo"
date: 2009-03-27
forum: General Help
---

### Post by lotusalive on 2009-03-27
hi guys and ladies too ( i assume ! ) :  :confused:

I was attempting to uninstall a program using:  

sol@sol-desktop:~$ sudo apt-get remove --purge mxallowd
[sudo] password for sol: 
Sorry, try again.
[sudo] password for sol: 

And my Password Has NEVER worked in Ubuntu 8.10.  

Does some one know WHY it does not recognize my password, or how I can get 

it to work ?  Thanks in advance for a reply.

:confused:

---

### Post by oldos2er on 2009-03-27
Are you the only user of this system? If so, you would use the password you first created at installation.

---

### Post by azzamite on 2009-03-27
Whas your user the first one to be created?
If so,
Are you using the **password of the curren user** (the same you use to login)?

In order to use sudo, you need to be in the group of sudoers.
(check with groups)

---

### Post by lotusalive on 2009-03-27
yes ma'am and sir, I'm the only user, and the password I created works for 

all other apps: ie: Login, Firestarter, Synaptic Pkg Mgr, just not in Accessories 

Terminal, which is the only terminal I utilize in Gnome...  I am the only 'current user' 

and so, my installation p/w is the only one I have...

Have had security troubles in past, should I go looking for a rootkit or

something ! ? ! ?

---

### Post by PrinceArithon on 2009-03-27
It sounds like a permissions issue...I have no idea what to tell you on that, but I suggest using synaptic to get rid of the program.

---

### Post by lotusalive on 2009-03-27
The program is mxallowd, and it WILL NOT uninstall from Synaptics !   It 

has no dependencies that are showing, but comes back with error 1 msg :  

post-installation script failed...


I will start a new thread on 'Permissions' Issue ? ?   Please Advise, 

Thanks. :confused:

---

### Post by oldos2er on 2009-03-27
Might want to look here: [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by lotusalive on 2009-03-27
Thx oldos2er, appreciate the link.  I will attempt to fix sudo with their

indicated command: adduser username admin

Although, I do not think I have ever deleted a user, much less an admin 

user!  So, am not sure why I have the problem, lol...

However, case in point, this is what happened after I worked on the 

System > Users & Groups > /root, and then did su to root and then ran 

remove --purge command:

root@sol-desktop:/home/sol# sudo apt-get remove --purge mxallowd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mxallowd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 274kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 239956 files and directories currently installed.)
Removing mxallowd ...
[: 19: 0: unexpected operator
You need to be root
invoke-rc.d: initscript mxallowd, action "stop" failed.
dpkg: error processing mxallowd (--purge):
 subprocess pre-removal script returned error exit status 1
[: 19: 0: unexpected operator
You need to be root
invoke-rc.d: initscript mxallowd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mxallowd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@sol-desktop:/home/sol# 

I'll be back after I try the sudo fix command...

---

### Post by lisati on 2009-03-27
<aside>When you type your password in after being prompted by sudo, it doesn't show....</aside>

---

### Post by oldos2er on 2009-03-27
"root@sol-desktop:/home/sol# sudo apt-get remove --purge mxallowd"

 Since you're running as root, you shouldn't need 'sudo' here. Try it without sudo and see what happens.

---

### Post by lotusalive on 2009-04-13
If anyone is still aware of this thread, I kind of gave up, but when I wanted to use gdebi to install RealPlayer11GOLD for linux tonight, it would not install the dependencies or the download, BECAUSE of mxallowd...

So, I went to use the command line to attempt to uninstall it again, results:

sol@sol-desktop:~$ root@sol-desktop:/home/sol# sudo apt-get remove --purge mxallowd
bash: root@sol-desktop:/home/sol#: No such file or directory
sol@sol-desktop:~$ su
Password: 
root@sol-desktop:/home/sol# sudo apt-get remove --purge mxallowd
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@sol-desktop:/home/sol# 

No other process is open on my desktop, and I don't know why this is, or what it means...):P

---

