---
title: "Customizing openssh"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Keymaster on 2006-10-03
I installed the package openssh-server in Synatpic Package Manager, and it runs, but I want to know a few things about it:

1.) How do I start/stop the ssh server on command?
2.) How do I change the port it runs on?
3.) How do I display a custom warning/disclaimer when a connection is established?
4.) Where is the config file for it?

This is very important since it is for remote administration of my server.  Thanks

---

### Post by skymt on 2006-10-03
> **Keymaster said:**
> I installed the package openssh-server in Synatpic Package Manager, and it runs, but I want to know a few things about it:

1.) How do I start/stop the ssh server on command?
2.) How do I change the port it runs on?
3.) How do I display a custom warning/disclaimer when a connection is established?
4.) Where is the config file for it?

This is very important since it is for remote administration of my server.  Thanks

1. "sudo invoke-rc.d sshd start" or "sudo invoke-rc.d sshd stop"

2. Edit /etc/ssh/sshd_config (sudo nano /etc/ssh/sshd_config). Toward the top should be a line that says "Port 22". Change that to whatever you like.

3. Put your warning/disclaimer in a file. Edit sshd_config, and put a line at the bottom like: "Banner /path/to/banner".

4. /etc/ssh/sshd_config

---

### Post by mitch.c on 2006-10-03
> **Keymaster said:**
> I installed the package openssh-server in Synatpic Package Manager, and it runs, but I want to know a few things about it:

1.) How do I start/stop the ssh server on command?
```
sudo /etc/init.d/ssh [start|stop]
```
> **Keymaster said:**
> 2.) How do I change the port it runs on?
```
# /etc/ssh/sshd_config
# Change nnnn to the port you want (default 22)
Port nnnn
```
> **Keymaster said:**
> 3.) How do I display a custom warning/disclaimer when a connection is established?
Create warning in /etc/issue.net, and then:
```
# /etc/ssh/sshd_config
Banner /etc/issue.net
```
> **Keymaster said:**
> 4.) Where is the config file for it?
/etc/ssh/sshd_config

> **Keymaster said:**
> This is very important since it is for remote administration of my server.

I suggest that you start by reading: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) and [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH) before you go too far. If you are going to open up ssh outside your private network, you need to fully understand what you are doing. You definitely need to use public key authentication.

Good luck.

---

### Post by Keymaster on 2006-10-04
Thanks.  That saves me soo much time searching for the files.  For some reason I neglected the etc folder.

---

