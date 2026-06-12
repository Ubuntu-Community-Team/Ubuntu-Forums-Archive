---
title: "Sudo su gives me a error"
date: 2006-10-04
forum: Desktop Environments
---

### Post by wenzlicker on 2006-10-04
I need a root terminal, so I type the following:

$ sudo su
Password:
configuration error - unknown item 'FAIL_DELAY' (notify administrator)
#

I get the root terminal, but what is the error all about?

---

### Post by timetunnel on 2006-10-05
First: root is disabled in a standard ubuntu installation, and if you don't **really** need it, you should leave it that way. Look here for details:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Second: I don't know what the error message means, but what do you want to achieve with "sudo su" at all? If you want to *execute **one** command as root*, you do "sudo command" (for example "sudo gedit /etc/apt/sources.lst"), and if you have the root account *enabled* and need to *work as root with **serveral** commands* in a terminal you just do "su" and you're there.

HTH
Jens

---

### Post by JGuru on 2006-10-05
First of all to get root priviledges use [color=blue]sudo, gksudo, gksu[/color] followed by 
command name. For eg., 
 
$ **sudo gedit /etc/X11/xorg.conf**

 This will open the xorg.conf file with root priviledges!!! So you read/ write
 do whatever!!

 If you do want to create a 'root' password & login as 'root'. Type:

 $[b]sudo passwd root
  (Enter new UNIX password)
  (Enter new UNIX password)[/b]

 Now login as root:

 $ [b]su -
  (Enter root password)[/b]

 Now you are logged in as 'root' Actually logging in as 'root' is very dangerous!!!
 Since any program can now run with root priviledges!!! So it's better to 
 use 'sudo'.

---

### Post by yota on 2006-10-05
FAIL_DELAY specifies how much a user has to wait after a wrong login attempt; it's contained in /etc/login.defs file.
```

#
# Delay in seconds before being allowed another attempt after a login failure
#
FAIL_DELAY              3

```
Maybe the file got broken: you can repair it by reinstalling the package 'login' which contains it, or have a look yourself.
```

yota@linbook:/etc$ dpkg -S /etc/login.defs
login: /etc/login.defs
yota@linbook:/etc$ dpkg -l |grep login
ii  login                                  4.0.13-7ubuntu3.2   system login tools

```
IMHO there's nothing wrong with 'sudo su': it's a safe way to become root. By the way the root account is not "disabled" it has just a random passoword, 'sudo su' or 'sudo -s' enable to become root using only the standard user's password.

Hope this helps.

---

