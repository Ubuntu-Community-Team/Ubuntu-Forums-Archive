---
title: "SSH, SCP Password"
date: 2009-03-22
forum: General Help
---

### Post by huruixd on 2009-03-22
Hi everyone,

Everytime using the command ssh or scp, i have to enter my password. I was wondering if there is a way making the terminal remembers my password.

---

### Post by ssam on 2009-03-22
best solution is probably using key based logins. there is loads of infomation on setting that up.

if you can't uses keys (my uni workstations and clusters dont allow keys), then you could try using a shared socket. this means the first ssh connection creates a socket, and as long as this is open, other connections go through the same socket.

[http://anothersysadmin.wordpress.com/2007/08/27/speed-up-openssh-connections-using-socket/](http://anothersysadmin.wordpress.com/2007/08/27/speed-up-openssh-connections-using-socket/)

---

