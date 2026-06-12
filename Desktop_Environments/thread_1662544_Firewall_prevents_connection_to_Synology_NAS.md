---
title: "Firewall prevents connection to Synology NAS"
date: 2011-01-08
forum: Desktop Environments
---

### Post by acag on 2011-01-08
I am having difficulty connecting to my new Synology DS211j NAS unit using **[COLOR=Blue]Connect to Server[/COLOR]**. When the ufw firewall is active, I receive the following error:

[COLOR=Red]Cannot open location "smb://myuserid@diskstation/backups/"
Failed to mount Windows share[/COLOR]

When the firewall is disabled, it works fine. Results of "sudo ufw status" command is:
Status: Active

9997:9999/udp     ALLOW     Anywhere
135,139,445/tcp   ALLOW     Anywhere
137,138/udp         ALLOW     Anywhere

Since I am a recent convert to LINUX, I need some assistance in troubleshooting this problem. Can someone school me in the activation and research of a log that will help diagnose my problem? I am not familiar with any of the logging mechanisms of LINUX. Any help will be appreciated.

Thanks,
acag




[COLOR=Red][/COLOR]

---

### Post by Frogs Hair on 2011-01-08
If you have the UFW GUI known as fire wall configuration installed from the software center , it is possible to set rules and enable logging which appears in the log file viewer.

---

### Post by Frogs Hair on 2011-01-08
Sorry ,link failed try these.

[http://www.cs.wcupa.edu/~rkline/Ubuntu/firewall.html](http://www.cs.wcupa.edu/~rkline/Ubuntu/firewall.html)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by acag on 2011-01-10
Thanks, Frog Hair! Using examples from the link you gave me, I entered the following command:

[COLOR=Red]Sudo ufw allow from x[/COLOR] (where x is the IP addr of my Synology NAS)

The [COLOR=Navy]Connect to Server[/COLOR] now works!!!!

---

### Post by endotherm on 2011-01-10
glad it worked out. looks like you were blocking access to samba. I have a very similar synology, and didn't have to do anything to make it work, but i had already installed samba on the boxes that were connecting so the samba install probably had already opened the ports. samba's data stream is udp based so makes sense that the allow would have to be bidirectional.

---

