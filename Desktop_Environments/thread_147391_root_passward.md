---
title: "root passward"
date: 2006-03-20
forum: Desktop Environments
---

### Post by thecat23 on 2006-03-20
Hi
  i am new to ubuntu and linux as well! As i started to use ubuntu 5.10, a whole bunches of problems jump out, can anyone help me out?
  1. what is the default root password, it didn't ask me to make up a root pswd while installation, only pswd i made is account pswd, what is the root password by default or is anywhere i can set up my own root pswd?
  2. how can i change the default resolution of the log in window? 
  3. where is the file that i can config the gateway and ip address?
Thanks a lot for helping me out. cheers!

---

### Post by paulipe on 2006-03-20
ok let me try and help:) 
In ubuntu there is no root user per se. Your account has the privileges of root. For example. If you want to create a new file

```
paulipe@paulipe:~$ touch /etc/paulipe
touch: cannot touch `/etc/paulipe': Permission denied
paulipe@paulipe:~$

```

In order to be able to do it as root all i have to do is
```
paulipe@paulipe:~$ sudo touch /etc/paulipe
Password:
paulipe@paulipe:~$

```
Ubuntu prompts for the password and then allows you to do whatever root can do. So there is no real need for root.

______
For screen resolution you can try System->Preferences->Screen Resolution
and System->Administration->Login Screen Setup

______
for networking you can go to System->Administration->Networking

---

### Post by halfvolle melk on 2006-03-20
Hi,
#1
You can do root stuff with sudo (see #3), but if you really want to you can set up a root password:
Open a terminal (Apps -> Accessories -> Terminal). Type
```
sudo su
<enter your user password>
passwd
<enter root password>
<enter root password again>
<press ctrl+c to exit root>
```
You can now access it by typing **su** in a terminal.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

#2 Don't know

#3
Open a terminal. Type
```
sudo nano /etc/network/interfaces
```
Edit it and safe the file. Mine looks like this (some of it anyway):

> # The primary network interface
iface eth0 inet static
        address 10.1.1.3
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 130.89.1.2

Edit: Forgot this. DNS can also be added to /etc/resolv.conf

---

