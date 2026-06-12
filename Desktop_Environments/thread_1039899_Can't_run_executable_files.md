---
title: "Can't run executable files?"
date: 2009-01-15
forum: Desktop Environments
---

### Post by kcredden on 2009-01-15
Oh boy, do I got a good one for you. Reciently I tried to update X-Plane, using their downloadable installer. I tried this once before, and it worked fine. But after a re-install of linux, I'm trying to re-install it, it doesn't work.

I click on "X-Plane Installer 123 Linux", and it does nothing.

I even do a "sudo X-Plane Installer 123" in a terminal, and it says 'command not found'

I rename it to xpi - same thing 'command not found'

Here is a  ls -la for it:

-rwxr-xr-x 1 root root 14278813 2008-01-29 15:45 X-Plane Installer 123 Linux

I even did a sudo -i and still get the same problem.

This is a total new install of Kubuntu (8.04.01) Have I missed some setting? I'm still a bit of a newb

- Kc

---

### Post by adamlau on 2009-01-15
```
chmod +x X-Plane Installer 123 Linux
sh X-Plane Installer 123 Linux
```

You may, or may not be able to get away with this without escalated privileges.

---

### Post by blackened on 2009-01-15
First do

```
chmod +x 'X-Plane Installer 123 Linux'
```

then

```
./'X-Plane Installer 123 Linux'
```

If it complains about sudo, then just preface the second command with sudo.

---

### Post by kcredden on 2009-01-16
Ok, tried both replies. Neither will work. 

adamlau: When I tried yours, I got a different error, that suggests that there's something wrong with the installer, and sent word to X-Plane's company about this. 

But blackened: I tried yours, got the same problem 'Command not found' 

I'll write back when I get it working. Probably there IS something wrong with the installer. It's odd. This is a re-install of linux, and before, I was actively playing X-Plane, but this time I'm getting a weird error.

Thanks for the help.

- Kc

---

### Post by taurus on 2009-01-16
Make sure you are in the directory where that file is.  Then, post the outputs of these commands.

```
ls -la 
file "X-Plane Installer 123 Linux"
```

---

### Post by 3rdalbum on 2009-01-17
Drag the file into a terminal window and execute it.

---

### Post by Midwestern_dave on 2009-04-11
I've tried loading X-Plane 9 from DVD Installer and had no luck.  I then tried the suggestions listed and when I do I get the following:

david@Dads:~/Desktop$ sudo chmod +x 'X-Plane DVD Installer Linux'
david@Dads:~/Desktop$ ./'X-Plane DVD Installer Linux'
./X-Plane DVD Installer Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory


I've tried:

david@Dads:~/Desktop$ sudo apt-get install libopenal.so.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libopenal.so.0
david@Dads:~/Desktop$

I've got 32bit Kubuntu 8.10 running on an AMD 64bit processor, any suggestions?

---

### Post by taurus on 2009-04-11
> **Midwestern_dave said:**
> I've tried loading X-Plane 9 from DVD Installer and had no luck.  I then tried the suggestions listed and when I do I get the following:

david@Dads:~/Desktop$ sudo chmod +x 'X-Plane DVD Installer Linux'
david@Dads:~/Desktop$ ./'X-Plane DVD Installer Linux'
./X-Plane DVD Installer Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory


I've tried:

david@Dads:~/Desktop$ sudo apt-get install libopenal.so.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libopenal.so.0
david@Dads:~/Desktop$

I've got 32bit Kubuntu 8.10 running on an AMD 64bit processor, any suggestions?

Try installing the libopenal1 package.

---

### Post by Midwestern_dave on 2009-04-14
> **taurus said:**
> Try installing the libopenal1 package.

I tried installing the libopenal1 package but it is already installed.

david@Dads:~$ sudo apt-get install libopenal1
[sudo] password for david:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libopenal1 is already the newest version.
The following packages were automatically installed and are no longer required:
  obex-data-server libnet-daemon-perl libdbi-perl libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0 libmaildir4 libplrpc-perl akonadi-kde akonadi-server
  libopenobex1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


Any other possible solutions?

Thanks

---

### Post by vlajkoral on 2009-05-06
```
$ cd /usr/lib
$ sudo cp libopenal.so.1 libopenal.so.0
```

---

