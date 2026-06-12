---
title: "Kubuntu sudo broken"
date: 2006-11-26
forum: Desktop Environments
---

### Post by steveM49 on 2006-11-26
I have been using Ubuntu for a couple of years with my "Linux in a Nutshell" book open in front of me.  I decided to try Kubuntu earlier this month.

In creating a symbolic link I screwed up my /home/user directory (I linked from /home/home/user instead).  It was corrected later that day.  In the meantime sudo began to give me problems.  From my administrative account, steveadmin, I can still open a root terminal session, so I have all the command line power available.  When I try to use a graphic interface, sudo acts like I have no SU capability.  The auth.log entry reads:
[INDENT]Nov 26 16:51:35  kdm: :0[4009]: (pam_unix) session opened for user steveadmin by (uid=0)
Nov 26 16:53:00  sudo: steveadmin : TTY=pts/3 ; PWD=/data/sda1/home/steveadmin ; USER=root ; COMMAND=/usr/bin/kdesu_stub -
Nov 26 16:53:00  sudo: steveadmin : TTY=pts/3 ; PWD=/data/sda1/home/steveadmin ; USER=root ; COMMAND=/usr/bin/kdesu_stub -
Nov 26 16:53:01  sudo: (pam_unix) auth could not identify password for [steveadmin]
Nov 26 16:53:01  sudo: steveadmin : pam_authenticate: Conversation error ; TTY=pts/2 ; PWD=/data/sda1/home/steveadmin ; USER=root ; COMMAND=/usr/bin/kdesu_stub -
Nov 26 16:53:09  sudo: steveadmin : TTY=pts/2 ; PWD=/data/sda1/home/steveadmin ; USER=root ; COMMAND=/usr/bin/kdesu_stub -
Nov 26 16:53:10  sudo: steveadmin : TTY=pts/2 ; PWD=/data/sda1/home/steveadmin ; USER=root ; COMMAND=/usr/bin/kdesu_stub -
Nov 26 16:53:11  sudo: (pam_unix) auth could not identify password for [steveadmin]
Nov 26 16:53:11  sudo: steveadmin : pam_authenticate: Conversation error ; TTY=pts/1 ; PWD=/data/sda1/home/steveadmin ; USER=root ; COMMAND=/usr/bin/kdesu_stub -
[/INDENT]
I've found the reference to the Troubleshooting Sudo site at [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo), but it doesn't seem to help.  My sudoers file is fairly simple:
[INDENT]#
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

#backuppc priveleges needs root access to tar for localhost
backuppc ALL=NOPASSWD: /bin/tar

#Add steveadmin
steveadmin ALL=(ALL) ALL
[/INDENT]
The etc/groups is similarly clean:
[INDENT]...
admin:x:113:steveadmin,steve
...
[/INDENT]
and /etc/hosts has the right entry for this computer:
[INDENT]127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.18 hestia
127.0.1.1 hestia[/INDENT]

So what can I do?  
From the root terminal I tried to create another administrative account and I have the same problems with that account that I have with steveadmin.

Any suggestions?

Thanks in advance
Steve

---

### Post by steveM49 on 2006-11-27
(bump)
I think the mistaken directory structure had a bad interaction with the hidden .kde subdirectory.

---

### Post by mexlinux on 2006-11-27
To run graphical programs you must use kdesu instead of sudo

---

