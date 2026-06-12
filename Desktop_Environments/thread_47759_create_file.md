---
title: "create file"
date: 2005-07-09
forum: Desktop Environments
---

### Post by dr1445 on 2005-07-09
Greetings Forum,
i just installed Kubuntu and tried to set up kpppd to dial the internet. i was greeted by the notice" /etc/resolv.conf is missing, have admin create the file, it can be empty".
i tried to enter the file as a folder in konqueror but that was a dead end due to permissions. that leaves the commandline as root. i do not know any code for the commandline. please supply the details on creating the file. the machine is 600mhz, 256ram, smartlink modem, cdrom player.
best regards
dave

---

### Post by crashtest on 2005-07-09
[QUOTE=dr1445]Greetings Forum,
i just installed Kubuntu and tried to set up kpppd to dial the internet. i was greeted by the notice" /etc/resolv.conf is missing, have admin create the file, it can be empty".
i tried to enter the file as a folder in konqueror but that was a dead end due to permissions. that leaves the commandline as root. i do not know any code for the commandline. please supply the details on creating the file. the machine is 600mhz, 256ram, smartlink modem, cdrom player.
best regards
dave[/QUOTE]

I don't really understand how it can be empty, but if that's the case, open a terminal and type 'sudo touch /etc/resolv.conf'  You will be prompted to enter a passwd.  Enter *your* password.  The result of this command is to create an empty file: /etc/resolv.conf.

If you know what the IP address of your DNS server should be, you could open a terminal, then type 'sudo gedit /etc/resolv.conf'.  Enter your password when prompted. The editor gedit will open.  Enter the IP address of your DNS server in this format: nameserver x.x.x.x where x.x.x.x is the IP address of the DNS server.  For example, my /etc/resolv.conf reads: nameserver 192.168.2.1.  Once you have done this, save the file.

Hope this helps.

---

### Post by dr1445 on 2005-07-09
great, should be just what is needed, acording to the kubuntu prompt. i will put that hdd back in the machine and take a swing at it in the AM.

---

### Post by angrykoala on 2005-09-05
I know this post is old, but I just installed kubu and 
have the same issue as well. I'll see if it works for me.

---

