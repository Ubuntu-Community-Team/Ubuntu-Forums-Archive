---
title: "How do I Secure SSH Between Two Computers?"
date: 2009-06-14
forum: General Help
---

### Post by Penguin Guy on 2009-06-14
[SIZE="5"]***Q:***[/SIZE] I am running SSH on two computers but would like to secure it a bit. I would like Computer A to deny all incoming SSH requests and allow all outgoing ones. I would like Computer B to allow incoming SSH requests **only** from computer A.

[SIZE="5"]***A:***[/SIZE] **Computer A:** Don't start the SSH server on the Computer A *or* add [COLOR="Green"]sshd: ALL[/COLOR] to /etc/hosts.deny
**Computer B:** Add [COLOR="Green"]sshd: ALL[/COLOR] to /etc/hosts.deny and [COLOR="Green"]sshd: <computer A's IP>[/COLOR] (example: [COLOR="Green"]sshd: 192.168.1.68[/COLOR]) to /etc/hosts.allow.

Thanks to everyone who replied.

---

### Post by lovinglinux on 2009-06-14
> **Penguin Guy said:**
> I would like Computer A to deny all incoming SSH requests and allow all outgoing ones. 

Just don't start the ssh server on the Computer A. The server doesn't have to be running to requests outgoing ssh connections.

> **Penguin Guy said:**
> I would like Computer B to allow incoming SSH requests **only** from computer A.

I would also like to know if it is possible to demand an extra password (and/or key) for users attempting to connect through SSH, and if so; how?

Thanks!

Use key authentication.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by nick125 on 2009-06-14
> **Penguin Guy said:**
> I am running SSH on two computers but would like to secure it a bit. I would like Computer A to deny all incoming SSH requests and allow all outgoing ones. I would like Computer B to allow incoming SSH requests **only** from computer A.

I would also like to know if it is possible to demand an extra password (and/or key) for users attempting to connect through SSH, and if so; how?

Thanks!

You can also use /etc/hosts.deny and /etc/hosts.allow to lockout SSH for anything except for the host you want. Add "sshd: ALL" to /etc/hosts.deny then add "sshd: <computer B's IP>", as in, "sshd: 192.168.1.150".

Of course, all of lovinglinux's suggestions would still apply :)

---

### Post by Iowan on 2009-06-14
Have you already changed to a non-standard port for SSH (something other than 22)?

---

### Post by Penguin Guy on 2009-06-15
Thanks for all the help guys. I'm sure I'll be able to figure it out from here. I'll post back if I have any problems.

:KS

---

