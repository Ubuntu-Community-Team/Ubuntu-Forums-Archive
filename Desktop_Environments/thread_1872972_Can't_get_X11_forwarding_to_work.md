---
title: "Can't get X11 forwarding to work"
date: 2011-10-31
forum: Desktop Environments
---

### Post by r.darwish on 2011-10-31
On my PC I have Ubuntu 11.10 64-bit installed. On my laptop I have Ubuntu 11.10 32-bit installed. I want to be able to forward X applications from my laptop to my PC using SSH.
I followed all tutorials but I can't get it to work.

sshd_config on the laptop contains the line:
```
X11Forwarding yes
```

It doesn't seem to work, however:
```

roey@roey-desktop:~$ ssh -X roey-1000h.local
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-12-generic i686)

 * Documentation:  https://help.ubuntu.com/

Last login: Mon Oct 31 20:30:25 2011 from 192.168.1.100
roey@roey-1000H:~$ firefox
Error: no display specified
roey@roey-1000H:~$ DISPLAY=:0.10 firefox

Error: cannot open display: :0.10

```

---

### Post by r.darwish on 2011-11-02
Anyone?

---

### Post by r.darwish on 2011-11-03
Did Ubuntu 11.10 break the X11 forwarding feature completly?

---

### Post by pavi_elex on 2011-11-03
Enable X11 forwarding (access other host through your terminal)
ssh username@hostname -X
or ssh username@hostname -Y

If you still get the “cannot open display” error, set the DISPLAY variable as shown below.
$ export DISPLAY='IP:0.0'  (without quotation)
IP is the local workstation’s IP where you want the GUI application to be displayed.

---

### Post by r.darwish on 2011-11-03
Thank you for replying. I tried -X and -Y and none worked. Setting the DISPLAY environment variable manually didn't work either.
I looked at auth.log and found a line that might indicate the problem:
```
Nov  3 19:37:24 roey-desktop sshd[23022]: error: Failed to allocate internet-domain X11 display socket.
```
Can anyone tell what does it mean?

---

### Post by r.darwish on 2011-11-03
I managed to solve this after a bit Googling. The cause was the fact that I disabled ipv6 on the server. As described [Here,]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/136947") I had to add sshd_config
```
AddressFamily inet
```

---

### Post by davidwhthomas on 2013-04-17
Thanks, I got X forwarding working over SSH well by

Editing my ssh config file at:
```
vim ~/.ssh/config
```

Adding the AddressFamily inet directive for, in this case, all hosts
```
Host *
    ForwardAgent yes
    AddressFamily inet
```

Displayed 32-bit remote app UI over X nicely.

---

### Post by oldos2er on 2013-04-17
Old thread closed.

---

