---
title: "Applications don't start"
date: 2006-06-25
forum: Desktop Environments
---

### Post by mickutz on 2006-06-25
Hi,

I have installed yesterday the Ubuntu 6.06. Everything worked perfect until half an hour ago, when I tried to give root permissions to my account by editing sudoers with visudo in recovery mode. I added my user to have all privileges but after I have rebooted nothing that, let's say, needed superuser acces, would work. It won't start any of the system or preferences applications and the network card doesn't take the settings by DHCP.

So could someone help me ?

](*,)

---

### Post by .t. on 2006-06-25
Type su in the terminal and see what output you get. Post it here. Do the same for sudo -s.

---

### Post by mickutz on 2006-06-25
this is the output:

su
Password:
su: Authentification failure


sudo -s
sudo: must be setuid root

---

### Post by .t. on 2006-06-25
Looks like you've mucked up your sudoers file. I don't really know enough about it to help further.

---

### Post by mickutz on 2006-06-25
[QUOTE=.t.]Looks like you've mucked up your sudoers file. I don't really know enough about it to help further.[/QUOTE]


Well, thanks for trying anyway.... now i'm waiting for other advices.

---

### Post by jimbob on 2006-06-25
Try:   sudo su

and enter your password like it asks.

I have had problems with the su command not recognizing a perfectly valid password for some time now.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...
_________________________________
[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by .t. on 2006-06-25
sudo -s is the same as sudo su.
I only suggested he try plain "su" as he has modified the sudoers file in an unorthodox way; su won't work on a standard Ubuntu system, as the root user is not given a password - just a random one known only by sudo.

---

### Post by mickutz on 2006-06-25
Seems that I'm going to reinstall it in the end because my work mates can't give any advices too..... well that will happen only if until tomorrow when I get home some will post the holy solution to my problem.

---

### Post by mlind on 2006-06-25
boot and choose recovery mode from grub menu.

edit your sudoers **only** using command
```

visudo

```

contents should look like
```

# /etc/sudoers
#
# **This file MUST be edited with the 'visudo' command as root.**
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

then add your useraccount to groups 
```

adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin

```

syntax is
```

adduser **user group**

```

---

### Post by mickutz on 2006-06-25
And after I do that, my network card will be able to retrieve the settings by DHCP and other appz work?

---

### Post by mlind on 2006-06-25
[QUOTE=mickutz]And after I do that, my network card will be able to retrieve the settings by DHCP and other appz work?[/QUOTE]

I don't think it will solve your DHCP problems, but it allows you to 'sudo' as root again.

---

