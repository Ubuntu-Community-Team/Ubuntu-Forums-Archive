---
title: "How to Configure 14.04 to Accept Simultaneous Remote Connections"
date: 2014-10-21
forum: Desktop Environments
---

### Post by schilders on 2014-10-21
We have a fresh installation of 14.04 on Amazon EC2.  We opened ports 5900 and 5901 on the Security group and installed vnc4server.  However, despite creating separate vnc users and modifying the configuration to see both users, we are still unable to connect simultaneously.  Can someone provide some documentation that would allow us to successfully allow more than one connection using VNCServer or something more compatible?  Thanks much for your help and guidance.

---

### Post by TheFu on 2014-10-21
Most VNCs dont' have any real security - plain text password and no encrypted transport. Best to be avoided for those reasons alone.

There is good news.  **x2go**.  Install the openssh-server, fail2ban (to protect your system from repeated hack attempts) and setup nominal ssh CLI connections first, then use the **x2go client** from any OS (Windows, Linux, OSX) to connect.  x2go uses ssh for authentication, creates an ssh tunnel per connected user and is 2-3x more network efficient than VNC or RDP - so the remote desktops behave much nicer.  There are some client-side options to make performance better - like using more jpg compression - this becomes more important as more users connect.

To more directly answer the port question - VNC needs a different port for every user - if you want 10 users, you'll need 10 ports. All non-secured.  Easier to use x2go with ssh - only 1 port needed for everyone.  If you want more even more security, don't allow ssh logins with passwords, only use ssh-keys and setup the sshd_config to disallow password-based logins.

Hope this helps.

There are other options depending on the needs, but I truly believe x2go is the best of all the available options.

---

