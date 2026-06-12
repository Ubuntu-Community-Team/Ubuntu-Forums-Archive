---
title: "Help with Terminal Server Client logon, please."
date: 2005-10-22
forum: Desktop Environments
---

### Post by L Campbell on 2005-10-22
I have a Compaq Presario (Pentium 11 350MHz) and a Smartlink (SL 1900 chipset) internal modem and I have the Ubuntu Live CD.

 I would appreciate some help configuring the Terminal Server Client.

Computer -  ?
Protocol  -   The default ?
User name  -  Would that be my e-mail address at my ISP ?
Password   -  Would that be the one I use with my ISP ?
Domain     -   OK, I have no idea.
Client Hostname  -  Again, no idea.
Protocol file  -  No idea here either.

If you can help me with some information in this area I would really appreciate it.

Thanks.

Lewis.

---

### Post by dbott67 on 2005-10-22
[QUOTE=L Campbell]I have a Compaq Presario (Pentium 11 350MHz) and a Smartlink (SL 1900 chipset) internal modem and I have the Ubuntu Live CD.

 I would appreciate some help configuring the Terminal Server Client.

Computer -  ?
Protocol  -   The default ?
User name  -  Would that be my e-mail address at my ISP ?
Password   -  Would that be the one I use with my ISP ?
Domain     -   OK, I have no idea.
Client Hostname  -  Again, no idea.
Protocol file  -  No idea here either.

If you can help me with some information in this area I would really appreciate it.

Thanks.

Lewis.[/QUOTE]

Terminal Services Client is an application that will allow you to remotely connect to a Windows Terminal Server, or in many cases now, a Windows XP Professional computer.  It does require that the 'host' computer (the one you want to remotely control) is running a program (XP Pro has a built-in 'terminal service'; you could also use VNC or some other similar service if you don't have XP Pro).

Suppose that you want to connect to a remote Windows XP Pro computer, such as your computer at work.  You *could* also use it to connect to a friend, neighbour or relative to offer some assistance, although the TS Client is not really for 'remote assistance' as it does not allow the remote user to see the desktop (although XP Pro also has an option for this, but it must be initiated by the remote user), it is more for accessing data file & resources on a work computer.  At work, I support 150 PCs and a dozen servers spread out over 4 locations.  Although I have many XP Pro computers, I use UltraVNC to remotely administer my network.  UltranVNC allows me to connect to any computer without any end-user intervention, as well as transfer files.  It allows me to see what the end-user sees and take control of their machine.

Anyhow, the settings are as follows:
- Computer: this is either the Netbios name or IP address of the computer you want to connect to.
- Protocol: RDP is the 'Remote Desktop Protocol'; there are others, such as using the TS Client to connect to a computer running VNC.
- Username: this would have to be a valid username on the remote PC, similar to the username you use to login to Ubuntu
- Password: this is the appropriate password for the above user account
- Domain: this would be required if you are logging on to a corporate network that uses Active Directory; otherwise you can leave it blank.
- Client Hostname: enter whatever the local hostname is of your computer (not the remote)
- Protocol File: optional; just leave it blank

If you've ever used programs like pcAnywhere, Laplink, GoToMyPC, VNC, etc. this program gives a similar type functionality --- it allows users to connect to remote computers that are great distances away and control the desktop.

-Dave

---

### Post by L Campbell on 2005-10-22
Thanks very much for your comprehensive reply, Dave.

It appears then, that I was totally in the wrong place.  All I wanted to do was to get access to the 'net, which was I was able to do very sucessfully on my other Linux system (Mepis), which uses KDE and the KPPP login system.

Is it _not_ possible to get online with Ubuntu and a dialup modem?

Kind regards.

Lewis.

---

### Post by stuporglue on 2005-10-23
It is possible.

Open the "Networking" from the System-->Administration menu. Is a modem listed there? If it was autodetected, you can just configure it there and you should be able to just hit "Activate"

---

### Post by L Campbell on 2005-10-23
[QUOTE=stuporglue]It is possible.

Open the "Networking" from the System-->Administration menu. Is a modem listed there? If it was autodetected, you can just configure it there and you should be able to just hit "Activate"[/QUOTE]

Thanks for your reply, Stuporglue.

I did as you explained and when I hit 'activate', 'deactivate' came alive.

However, it never did connect to my phone, so I didn't get online.

Under the 'Properties', 'General' tab I feel that I have the correct information.

Under 'Modem' I had to change from /modem to /ttyso

Under the 'GENERAL' tab the default is Ubuntu but I don't know what should go in 'Domain'.

Both sections under 'DNS' are empty and I'm not sure what 'Hosts' is all about.

Anyway, I feel like I'm heading in the right direction.

All I want to do is to get online and I have no interest in setting up a network.

Thanks again for your help.

Lewis.

*****

---

