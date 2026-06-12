---
title: "[SOLVED] Internet connetion fails through the terminal"
date: 2008-09-21
forum: Desktop Environments
---

### Post by maruthi_s@infosys.com on 2008-09-21
[COLOR="Blue"]
[FONT="Verdana"]
Dear Ubuntu Geeks, 

I am using Ubuntu 8.04 LTS Desktop edition. 

Connection to the Internet through the browser is working fine. I am connecting to the net through the LAN network and it prompts for a user id and password when I connect to Internet. 

Connecting to net through the Terminal is failing because it could not retrieve the login information. Kindly let me know how do I fix this issue. 

Thanks in Advance 



[/FONT][/COLOR]

---

### Post by marcthenarc on 2008-09-21
"Connecting to net through the Terminal" needs clarification.  Are you talking about the command line console (with the aid of Konsole or xterm) or some application named this way ?

Receiving a password prompt to connect your browser to the world sounds like you are behind a corporate firewall that requires authentification or a crafty little home router.  In either case, the problem come from relaying your request through firewall rules. I don't think ubuntu has such rules by default (but I'm open to suggestions and rebuttals).

If you can access the net through a browser, what kind of applications are you trying to use through the terminal : lynx ? How about other services like 110 (pop3) for your email ?  22 (ssh) to a remote machine ? Maybe your provider / sysadmin will also limit some ports.

Try 'ping ubuntuforums.org' to check for ping services on your network.
Try 'lynx ubuntuforums.org' to check for non-graphical web access.

You can also use telnet <ip adress> <port> (fill in your own values) to see which services are available on your network.

Bring down the problem to specifics.

Good luck.

---

### Post by maruthi_s@infosys.com on 2008-09-21
Thanks for the reply Mac, 

The terminal I meant here is the command prompt of Ubuntu that comes from the Application->Accessories->Terminal. 

Yes you are right, I am in the corporate environment and when I connect to net through the browser, I connect through the domain/username with the password. 

Kindly let me know how do I give the same/configure the same  while I am accessing some sudo apt-get install commands for installing ubuntu updates. 

Thanks in advance.

---

### Post by Patrick793 on 2008-09-21
In the terminal, when Sudo asks you for a password, you enter the password you use to login to your computer with. Not the password for the corprate domain.

---

### Post by maruthi_s@infosys.com on 2008-09-21
Hi Patrick,

I am entering the password of the ubuntu Administrator only and not the domain one. 

I am wondering whether sudo pppoeconf will be able to resolve this issue .. Because that is for ADSL. I am scared to use that, of which my network settings might get changed. 

Thanks 
Maruthi S

---

### Post by maruthi_s@infosys.com on 2008-09-23
[COLOR="Blue"]

Hi All,

The issue got resolved. This issue is due to the network proxy settings where i mentioned the proxy details and authentication details. Now terminal is able to connect to the Internet and download the files.

Thanks for all your Help

[/COLOR]

---

