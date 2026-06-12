---
title: "sudo and root privileges to do some tasks"
date: 2005-04-09
forum: Desktop Environments
---

### Post by plockery on 2005-04-09
Hi!

I have just installed and have been fiddling around for a while now.
I have a small homenetwork with my printer and data on another windows 2000 pc.

It took me a while to get my head around the whole sudo thing, but I think i have it now.

Except I get the impression that this new system should allow you to do everything necessary to tinker with your system.

There are at least two things i want to do that I cant do right now.

1. I cant install a printer through cups (localhost:631). I think Cups always wants a root login and password to allow you to manage printers.

2. I can't seem to run the samba daemon "/etc/pam.d/samba start". It doesn't recognise the command if I put sudo in front of it. And if I run it from a terminal whether from myself or root it then says permission denied.

Is it possible to do both these and anything else with root privileges without setting a root password and / or enabling the root account?
If not I'm not sure in the end what benefit sudo has over the old system!

Thanks in anticipation

---

### Post by jdong on 2005-04-09
1. Use a built-in configuration tool to manage CUPS, such as the GNOME/KDE CUPS tools. The CUPS admin interface is an awesome way for someone to capture your root password :)

2. Did you *install* samba? (apt-get install samba). By default, only the samba CLIENT is installed, not the server. BTW, it's /etc/**init.d**/samba start, /etc/pam.d/samba stores authentication/restriction settings for Samba users.

---

### Post by plockery on 2005-04-09
Thanks for the help.

Re Samba. how dumb! Never even thought that it might not be installed! Installed it and started it no problem. I did think it was strange that it was not in /etc/init.d but it never twigged!!

Can you tell me the command in ubuntu's sytem to have samba start at bootup?

Re cups. by cups tools do you mean for example the kde print manager? I would still like to be able to get into cups via the localhost option. Can you tell me how to do this?

---

### Post by jdong on 2005-04-09
[QUOTE=plockery]
Can you tell me the command in ubuntu's sytem to have samba start at bootup?

Re cups. by cups tools do you mean for example the kde print manager? I would still like to be able to get into cups via the localhost option. Can you tell me how to do this?[/QUOTE]

By default, after Samba installs, it'll start by default. See [http://ubuntuforums.org/showpost.php?p=122821&postcount=3](http://ubuntuforums.org/showpost.php?p=122821&postcount=3) for information about boot-time service configuration.

CUPS: Yes, I mean like the KDE print manager. We've had discussions here in late-2003 about enabling the CUPS admin interface. I don't remember which post of the 100,000+ here it was (pardon me). Please search and see if you can locate it. Again, it's not a very security-wise decision. :)

---

### Post by plockery on 2005-04-09
Thanks again.

I have found some posts stuff about the cups interface.

Much appreciated.

---

### Post by nad on 2005-04-09
To manipulate smb services, the command is '/etc/init.d/samba option' where option is one of {start|stop|reload|restart|force-reload}. Or you can use the gui menu options under Computer -> System Configuration -> Networking -> General and enable WIndoz Networking.

The New Printer gui works fine and there is a "Become Administrator' button in the printer properties menu if you need it. Just remember to change the network protocol to 'Windoz Printer (SMB). You may have a protocol or authentication issue on the win2000 machine or a driver issue with ubuntu.

This is of course assuming that you have set up SMB users and passwords correctly.

Dan M

---

