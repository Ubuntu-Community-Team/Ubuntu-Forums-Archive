---
title: "ssh browser?"
date: 2007-09-23
forum: Desktop Environments
---

### Post by Jagged on 2007-09-23
is there some way i can browse my server with a browser over ssh? the client is using windows which is why this problem exists. my windows client is using putty to connect

---

### Post by jrib on 2007-09-23
I'm not sure what you mean here by "browser."  Can you explain?

If you want to ssh like you do in putty, just make sure the "openssh-client" package is installed and in a terminal do ```
ssh username@host
```
where "username" is your username and "host" is your host of course

---

### Post by SmokinJuan on 2007-09-23
[http://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe]("http://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe")

---

### Post by Jagged on 2007-10-05
i want to use a file browser over ssh through putty.

---

### Post by jrib on 2007-10-05
In Nautilus, File -> Connect to Server
Select "SSH" as the type

---

### Post by D-EJ915 on 2007-10-06
> **Jagged said:**
> i want to use a file browser over ssh through putty.
well you can't just run X programs through putty, you'd have to use some sort of X emulation of sorts, like cygwin to actually *run* the program.  The way I do filesystem over ssh is sshfs, but that might be kind of intertesting to get working on a windows system.  I can't really help you more than that sorry to say, I've never bothered with cygwin before, I use windows like 3 times a month.

---

