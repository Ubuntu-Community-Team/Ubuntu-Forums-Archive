---
title: "vncviewer (from Ubuntu to XP Home)"
date: 2005-12-27
forum: General Help
---

### Post by PilotEd on 2005-12-27
Greetings...I have a 2 PC lan (1 XP Home and 1 Ubuntu) connected with a Linksys BEFSR41 firewall/router.  I'm using TightVNC on the XP PC and can connect to the Ubuntu PC very nicely.

I'm trying to connect from the Ubuntu PC to the XP PC (I don't have XP Pro) using vncviewer.  I'm using Ubuntu "out of the box".

I've disabled the Windows firewall and Norton anti-virus on the XP box.  I've been able to setup an ftp server on the XP PC and using commandline ftp from the Ubuntu PC have been able to access the FTP server on the XP PC so the lan is working properly.  I'm not trying to cross the firewall but using a lan-only solution (I also am using IP addresses as I don't have DNS running on the lan).

I can launch vncviewer from the Ubuntu PC using a terminal window and specifing the IP address of the VNC server to connect to (IP's - XP is 192.168.1.100 and Ubuntu is 192.168.1.101),  but get the following: "vncviewer: ConnectToTcpAddr: connect: Connection refused".

I've googled for hours on this one and am at a loss as to what to do.  Most of what I've read is to allow PC's and Ubuntu on opposite sides of a firewall to communicate.  I haven't been able to locate much in regards to a lan only setup.

Suggestions?  Thanks in advance...

---

### Post by pharcyde on 2005-12-27
What versions of the software are you using on both machines?

Meaning what vnc client and server are you using for windows?

What vnc client and server are you using for ubuntu?

There are various vnc servers for windows that should work fine with any client since vnc is a pretty std protocol.  Make sure you are specifying the correct vnc port for the server. (i.e.  192.168.1.100:5900 to connect to windows machine assuming its running on port 5900)  Most of the vnc servers for windows I've used have defaulted to port 5900.

If you still have problems try running different vnc servers.  A few are listed below.

[http://www.realvnc.com/](http://www.realvnc.com/)
[http://www.tightvnc.com/](http://www.tightvnc.com/)
[http://ultravnc.sourceforge.net/](http://ultravnc.sourceforge.net/)

---

### Post by PilotEd on 2005-12-27
The version of TightVNC (client and server) being used on XP Home is 1.2.9 (the latest version from tightvnc.com).  The vncviewer being used on Ubuntu is 3.3.7.

The ports for both the vnc server and client are 5900.

For grins, I started the vncviewer on the Ubuntu PC (using the vnc server from the Ubuntu PC) by specifying the Ubuntu IP address.  The result is the Unbuntu display being cascaded several times so the client software is communicating with the server software (on the Ubuntu PC).  I then performed the same test on the XP PC but could not get the client to communicate with the vnc server on the XP PC (the XP PC appears to not be accepting a client request).  Shouldn't the XP PC behave the same way as the Ubuntu PC when both client and server are on the same hardware?

Hmmm.....

---

### Post by PilotEd on 2005-12-27
Problem resolved by switching to UltraVNC...I can access my XP PC from my Ubuntu PC and vice versa...

---

