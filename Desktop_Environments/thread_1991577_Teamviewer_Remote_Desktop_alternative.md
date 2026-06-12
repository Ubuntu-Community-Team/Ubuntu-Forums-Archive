---
title: "Teamviewer Remote Desktop alternative"
date: 2012-05-30
forum: Desktop Environments
---

### Post by Lyfang on 2012-05-30
Hi, Teamviewer is not a Linux native application, it has built-in Wine ([http://www.winehq.org](http://www.winehq.org)). I would also like to connect to a Windows environment with a Remote Desktop application. What application can handle RDP, VNC and SSH protocols & is Open Source? Would this application connect through a home network connection? I also want to hear audio...

grdesktop can handle Remote Desktop Protocol (RDP) but what about? "Step-by-Step Guide to Remote Assistance"? [http://www.linuxhomenetworking.com/forums/showthread.php/16002-Step-by-Step-Guide-to-Remote-Assistance](http://www.linuxhomenetworking.com/forums/showthread.php/16002-Step-by-Step-Guide-to-Remote-Assistance)

What about the IP address, router port, SSH tunnel? 

How can Windows users easily connect to a Linux RDP server? xrdp?

See also: [http://alternativeto.net/software/teamviewer/?platform=](http://alternativeto.net/software/teamviewer/?platform=)

---

### Post by Sularco on 2012-06-01
Teamviewer is a proprietary application free for private use. It runs very well on Linux (using, as you say, Wine to run the Windows binaries). I had good experience with it helping out people who were using other platforms than Linux, as it is easy to install for inexperienced computer users. But there is no bidirectional sound.

Remote Assistance is a Windows-only tool. I am unaware of any Linux application having ever been written to interface with it. But that should pose no problem as the xrdp server running on a Linux machine will allow a Windows user to log into the Linux desktop. However xrdp is (not yet) capable of bidirectional sound transfer. I would recommend to limit the use of xrdp to the local LAN, as the maximum encryption strength is currently only 128 bits. For use over the internet I'd propose to set up a secure VPN line first.

For logging into a Windows Terminal Server from a Linux PC I have successfully used the Vinagre package from my Lubuntu desktop.
Another option for achieving what you want is VNC. As the server as well as the client platforms are usually multi-platform, interconnections between PC's using different operating systems should be easily achievable. It is also possible if necessary to set up the Linux PC so that it generates a seperate display for the remote client to log in (i. e. the remote user does not log into the Linux PC's monitor, mouse and keyboard, but instead is using a different user-session). I have configuration files ready for that if you need them.

For a Linux-to-Linux PC connection you can also use a secure ssh connection:

```

ssh -X -C -c blowfish username@192.168.0.100 gnome-panel

```

This will open a gnome desktop from the remote machine on the local machine - very slick.
Replace the IP address 192.168.0.100 with the IP address of the destination PC and the "username" with the username you want to use on the remote machine. For this to work the package openssh-server must be installed on the destination machine.

---

