---
title: "Low graphic, PC couldn't start"
date: 2012-11-30
forum: Desktop Environments
---

### Post by satimis on 2012-11-30
Hi all,

Host	Ubuntu 12.04 desktop 64bit
VM	Ubuntu 12.04 server 64bit
Virtualizer	Oracle VirtualBox

I followed;
Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 12.10)
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.10)

installing the LAMP server on the VM running remote installation on the host terminal vis ssh.  It worked without problem.  After having finished "1 Preliminary Note" I took a break with the PC switched off.

After the break I started the PC and the server on the VM.  Unfortunately I forgot to run;
$ ssh user@192.168.0.101
on the host terminal to login on the server.

Then I followed "2 Install Postfix, Courier, Saslauthd, MySQL, phpMyAdmin" installing;```

$ sudo apt-get install postfix postfix-mysql postfix-doc mysql-client mysql-server courier-authdaemon courier-authlib-mysql courier-pop courier-pop-ssl courier-imap courier-imap-ssl libsasl2-2 libsasl2-modules libsasl2-modules-sql sasl2-bin libpam-mysql openssl phpmyadmin apache2 libapache2-mod-php5 php5 php5-mysql libpam-smbpass

```
installing those packages on the host terminal and finished up to "4 Create The MySQL Database For Postfix/Courier".

Then I realised having made this mistake installing those packages on the host.  I started removing the installed packages on host terminal by;

1)
$ apt-get remove postfix
(no problem)

2)
$ sudo apt-get phpmyadmin apache2 libapache2-mod-php5 php5 php5-mysql
(also no problem)

3)
IIRC on running;
$ sudo apt-get openssl

I was NOT allowed to remove it, suggesting to run "autoremove"

On running;
$ sudo apt-get autoremove openssl
Suddenly I saw it starting removing GNOME packages.

I could not stop the action even with the terminal closed.  

I switched to F3 (Text Mode) and rebooted PC.  But I could not started the host, warning low graphic.

I think I could start rescue mode dropping to shell.  Please help how to rescue this PC.  There are about 20 VMs running on this box.

TIA

B.R.
satimis

---

### Post by Isamu715 on 2012-11-30
Try reinstalling the packages you removed with the autoremove command. To see what exactly got removed check */var/log/dpkg.log*, If you can't get an Internet connection in recovery mode check if the packages you need are still present in */var/cache/apt/archives*. Then you can install them using:
```
dpkg -i packagename.deb
```As for the VMs I think it's possible to backup them from a LiveCD.

---

### Post by satimis on 2012-11-30
> **Isamu715 said:**
> Try reinstalling the packages you removed with the autoremove command. To see what exactly got removed check */var/log/dpkg.log*, If you can't get an Internet connection in recovery mode check if the packages you need are still present in */var/cache/apt/archives*. Then you can install them using:
```
dpkg -i packagename.deb
```As for the VMs I think it's possible to backup them from a LiveCD.

Hi,

Thanks for your advice.

I already fixed the problem with following steps;

1) Booted to Init-1
2) Ran;
$ sudo apt-get install --reinstall ubuntu-desktop
$ sudo reboot

Ubuntu desktop is now coming back.

satimis

---

