---
title: "block internet for program?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-10-25
is there a way, in ubuntu breezy, to block internet for a certain program?

---

### Post by fannymites on 2005-10-25
Depending on the program you want to block you could use guarddog firewall to block the protocol it uses eg bittorrent, chat programs.  Unfortunately it would also block other apps of similar types.
This is something I've been looking for though, a Kerio style firewall for linux.

---

### Post by dbott67 on 2005-10-25
If you know the port number that the application uses, you can use a firewall to block access to that port.  Any traffic that attempts to send outbound traffic on that particular port would be blocked.

I don't think Firestarter can block specific outbound ports, but perhaps someone else knows of a better one that offers more flexibility.

EDIT:  It looks like fannymites beat me to the punch! :)

-Dave

---

### Post by HermanAB on 2005-10-25
Hi there,

As usual, there are various ways to skin this cat:

Daemons that were compiled with libwrap, can be blocked with tcpwrappers in hosts.allow or hosts.deny.  See 'man hosts.deny'.

Otherwise, you can drop communications on  a specific port using Netfilter:
# iptables -I INPUT -i eth0 -t tcp --dports blockedportnumber -j DROP

Another way, is to block the destination host in the /etc/hosts file:
[www.cnn.com](www.cnn.com) 127.0.0.1

That breaks the DNS system, so then CNN cannot be reached.

The final method is with squid-cache and Access Control rules.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by DarkManX4lf on 2005-10-26
hmm i tried these but i couldnt find the port for the program andi didnt want to mess with the hosts thing...but is there a way to set a hot key to disable and enable my eth0 ?

---

### Post by dbott67 on 2005-10-26
To find the port number the application uses, open the application and use it normally.  Then open a terminal and use the **netstat** command.
```
netstat -a
```
and then look through the list to see if you can find the port of the application.  Check the man pages for netstat to see other switches and options.

As for quickly enabling and disabling the eth0, you could write a script and assign a hotkey to run it (or just double-click it).

To make a script to disable eth0:[LIST=1]
[*]From a terminal type:
```
gedit ~/Desktop/off.sh
```
[*]In the editor, type the following:
```
#!/bin/bash
sudo ifdown eth0
```
[*]Save & make executable.[/LIST]To make a script to enable eth0:[LIST=1]
[*]From a terminal type:
```
gedit ~/Desktop/on.sh
```
[*]In the editor, type the following:
```
#!/bin/bash
sudo ifup eth0
```
[*]Save & make executable.[/LIST]You'll have 2 icons on your desktop, on.sh & off.sh.  Double-click either one to enable/disable.

-Dave

---

### Post by DarkManX4lf on 2005-10-26
[QUOTE=dbott67]To find the port number the application uses, open the application and use it normally.  Then open a terminal and use the **netstat** command.
```
netstat -a
```
and then look through the list to see if you can find the port of the application.  Check the man pages for netstat to see other switches and options.

As for quickly enabling and disabling the eth0, you could write a script and assign a hotkey to run it (or just double-click it).

To make a script to disable eth0:[LIST=1]
[*]From a terminal type:
```
gedit ~/Desktop/off.sh
```
[*]In the editor, type the following:
```
#!/bin/bash
sudo ifdown eth0
```
[*]Save & make executable.[/LIST]To make a script to enable eth0:[LIST=1]
[*]From a terminal type:
```
gedit ~/Desktop/on.sh
```
[*]In the editor, type the following:
```
#!/bin/bash
sudo ifup eth0
```
[*]Save & make executable.[/LIST]You'll have 2 icons on your desktop, on.sh & off.sh.  Double-click either one to enable/disable.

-Dave[/QUOTE]


thanks how would i assign the hot key to it?

---

### Post by dbott67 on 2005-10-26
[quote=DarkManX4lf]thanks how would i assign the hot key to it?[/quote]

You may have to search the forums, but there is a setting in the "Configuration Editor" that allows you to create 'key bindings'.

I have not done this myself, so I'm a little unsure how to assign a script to it.  There is also a setting for KEYBOARD SHORTCUTS under SYSTEM --> PREFERENCES.  This seems to have a list of applications & activities, but I do not see how to add new ones (perhaps that where the "keybindings" comes in in the Congifuration Editor).

-Dave

---

### Post by dbott67 on 2005-10-26
[quote=dbott67]You may have to search the forums, but there is a setting in the "Configuration Editor" that allows you to create 'key bindings'[/quote]

[FOUND ONE]("http://www.ubuntuforums.org/showthread.php?t=79560&highlight=create+keyboard+shortcut").

-Dave

---

### Post by fannymites on 2005-10-26
There is an application based firewall for linux , TuxGuardian.  Now you can choose which apps to block or allow.
[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)
I haven't tried it yet but I'm gonna.

---

### Post by DarkManX4lf on 2005-10-26
[QUOTE=fannymites]There is an application based firewall for linux , TuxGuardian.  Now you can choose which apps to block or allow.
[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)
I haven't tried it yet but I'm gonna.[/QUOTE]

thanks i'll try the firewall in a minute, but first i want to get this hot key thing working....ok so here is what i did i created the off.sh (which disables eth0) and on.sh (which enables eth0), i went to the Configuration Editor and  i went to apps>metacity>keybinding_commands, i went to command_1 and i set the value to "sudo sh ./root/Desktop/off.sh" and then i went to apps>metacity>global_keybindings and for run_command_1 i set it to <Alt>z (which i assume is ALT+z ?) and i close the Configuration Editor but when i press  ALT+z it doesnt work nothing happens...i can double click on the file and it works but if i use the hot key thing it doesnt run i guess, how do i fix this?

---

### Post by DarkManX4lf on 2005-10-27
nevermind i got it to work i had to put /Desktop instead of /root/Desktop, thanks guys.

---

