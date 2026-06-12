---
title: "Can't Launch From Konsole...Why?"
date: 2005-04-01
forum: Desktop Environments
---

### Post by coolbreeze on 2005-04-01
I remember this was a problem for me when I installed Ubuntu but I can't remember how I fixed it.

I just installed Kubuntu and loving it.  But I have one problem.  Although I am logged in konsole as root I can't initiate graphical applications from the terminal.  I receive a message that says "connection to server refused".  When I create a link to the application on the desktop the link works!  Or if the application can be launched from the K Menu it also works! 

Why can't I launch from the konsole?

---

### Post by silent82 on 2005-04-01
I have the same problem!!!

But I can't launch applications from K-Menu or from the Desktop.

This is stopping me from using KDE.

Tried to delete all .DCOPserver* files from my home and   /var/tmp/kdecache-* 
but still have this problems...

---

### Post by coolbreeze on 2005-04-01
I'm at work right now and don't have access to my Linux.  I wished I did because I just read in another forum that someone fixed this problem by simply doing the following in konsole:

xhost +localhost 

Does this work?

---

### Post by silent82 on 2005-04-01
[QUOTE=coolbreeze]I'm at work right now and don't have access to my Linux.  I wished I did because I just read in another forum that someone fixed this problem by simply doing the following in konsole:

xhost +localhost 

Does this work?[/QUOTE]
 it doesn't work... at least for me...
anyway this is the error message
```
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/silent82/.DCOPserver_port0__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
WARNING: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ERROR: KUniqueApplication: Can't setup DCOP communication.
```

---

### Post by fdoving on 2005-04-01
For simply running X applications as root.. on a user Xsession xhost is the solution. Based on the error you might have other problems.. but anyway:
```

xhost +local:

```
should do it.. or just 'xhost +', if you want to disable the access control.. make sure you're firewalled or preferably tcp is disabled for your X server.
'xhost -' to re-enable access control.

Found a much better way to do this.. 'xhost +local:' is by far the best way for all local users to be able to connect.. without caring about the network stuff.

---

### Post by coolbreeze on 2005-04-01
Cool!...I'm anxious to get home and try it!

Update:  It worked!!  My problem is solved! Thanks

---

### Post by silent82 on 2005-04-01
[QUOTE=fdoving]For simply running X applications as root.. on a user Xsession xhost is the solution. Based on the error you might have other problems.. but anyway:
```

xhost +root

```
should do it.. or just 'xhost +', if you want to disable the access control.. make sure you're firewalled or preferably tcp is disabled for your X server.
'xhost -' to re-enable access control.[/QUOTE]
 Doesn't work for me :(

UFFFFFFFF!!!!

---

### Post by fdoving on 2005-04-01
[QUOTE=silent82]Doesn't work for me :(

UFFFFFFFF!!!![/QUOTE]
 try again with the changes i've made to my original post!

---

### Post by fdoving on 2005-04-01
just for clearity.. xhost commands are to be executed as the user running the Xsession.. not root or anything..

---

### Post by silent82 on 2005-04-01
I did all listed but nothing worked... still giving me problems... waiting for stable kubuntu cd so I will re-install all the system.

Tanks!

---

### Post by fdoving on 2005-04-01
what's your problem? if you can explain what you do.. and put the errors here.. maybe i can help.

---

### Post by silent82 on 2005-04-01
[QUOTE=fdoving]what's your problem? if you can explain what you do.. and put the errors here.. maybe i can help.[/QUOTE]

Before I login I press ctrl + F1 so I open the shell. I login in text mode and, as root, I type, from my home dir:
  rm -rf .DCOP*
  rm -rf .kde*
  rm -rf .qt*
  rm -rf /var/tmp/kdecache*

Then I login in KDE3.4 and the "first-time configuration" wizard opens. I just press on "NEXT" and, at the end, on "FINISH". KDE now continues loading and all works well. I can open Control Center from K-Menu and all icons on the desktop. Now I open Konsole and all loads OK. Now I type
  kcontrol
and here is the error:
```


DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/silent82/.DCOPserver_port0__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
WARNING: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ERROR: KUniqueApplication: Can't setup DCOP communication.

```

Now if I try to open any of the file or folder on the  desktop a window pops up:
  "KLauncher could not be reached via DCOP"

The desktop does not freezes but I can't lounch any application.

This same error comes up also if I don't open konsole, but, in this case, the error comes up in an unpredictable moment.

This error keeps me away from using KDE.

I thank all for any help.

---

### Post by fdoving on 2005-04-01
Looks like your problem is that dcopserver is crashing somehow.

while kde is running.. if you can start konsole.. and try to remove the .DCOP files.. as dcopserver suggests.
and then try to run dcopserver manually:
```

dcopserver --nosid

```


are you using the newest KDE in the ubuntu repositories?
If not, try to upgrade:

apt-get update;apt-get -u dist-upgrade

---

### Post by silent82 on 2005-04-01
OK. I did remove all .DCOP* files and runned

```

dcopserver --nosid

```

but still have the same problem.

I have the latest Ubuntu hoary. Just did
apt-get update
apt-get dist-upgrade

---

### Post by fdoving on 2005-04-01
my last $0.05.. re-install kdebase-bin.

```

apt-get --reinstall instal kdebase-bin

```

---

### Post by silent82 on 2005-04-01
Oh well... it didn't work! It's a strange thing...

Thanks for the help!!

---

### Post by Ankur Dave on 2006-08-24
This is probably a bit late...but I had the same problem. Check the owner of ~/.kde/. For me, the owner was root and permissions were rwx------. Doing `sudo chown -R <myusername>:<mygroup> kde/` fixed the problem completely.

---

### Post by vipersniper on 2008-04-25
I can't guarantee this will help everyone, but in my case this occurred when I upgraded to Ubuntu 8.04 from 7.10 because my computer was part of a domain, however the installation cleared the domain name from my network config, while leaving my hosts file alone. Thus whenever anything required sudo, sudo was looking up <computername> rather than <computername>.<domainname> , which was in the hosts file, adding my domain back into the network config fixed the problem.

---

### Post by pbhj on 2008-04-28
> **vipersniper said:**
> I can't guarantee this will help everyone, but in my case this occurred when I upgraded to Ubuntu 8.04 from 7.10 because my computer was part of a domain, however the installation cleared the domain name from my network config, while leaving my hosts file alone. ...

Vipersniper, can you say where you can check and what exactly was missing from the network config?

This was probably my issue, however it seems to work by doing "xauth list" as user, then "xauth add $AUTHSTRING" as root, where $AUTHSTRING is the host, display and auth info from the previous line.

It didn't work by doing "xhost +localhost".

That might help someone too.

---
The xauth stuff appears to get reset on reboot / X restart. [Another post]("http://ubuntuforums.org/showthread.php?t=166863&highlight=xhost+local&page=2") suggested to add > env_keep+="DISPLAY XAUTHORITY" to the Defaults line of your /etc/sudoers file, which I'm trying now (PS: I edit sudoers with nano, as I hate Vi, and then check with "visudo -c").

---

