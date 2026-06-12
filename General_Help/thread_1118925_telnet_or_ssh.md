---
title: "telnet or ssh?"
date: 2009-04-07
forum: General Help
---

### Post by abhilashm86 on 2009-04-07
most people say ssh is more secure than telnet, so which one of these is bettr to use to login onto a dumb server? Like our machine should not become a threat when connected to outside machine...............

---

### Post by kpatz on 2009-04-07
The issue with telnet is everything is transmitted in plain text, including your login password.  While this is especially dangerous over the internet, even on a LAN someone could sniff your password.

ssh is more powerful/flexible as well (for example, you can use scp or sftp to transfer files, sshfs to mount shares, tunnels, etc.).  I see no reason to use telnet, unless you have an old server that has no support for ssh.

---

### Post by abhilashm86 on 2009-04-07
> **kpatz said:**
> 
ssh is more powerful/flexible as well (for example, you can use scp or sftp to transfer files, sshfs to mount shares, tunnels, etc.).  I see no reason to use telnet, unless you have an old server that has no support for ssh.

yes i get the point, now i'm reading documentation of ssh, i think it'll good to use ssh, i want a link to get to know about ssh usage........

---

### Post by xang on 2009-04-07
> **abhilashm86 said:**
> yes i get the point, now i'm reading documentation of ssh, i think it'll good to use ssh, i want a link to get to know about ssh usage........

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

