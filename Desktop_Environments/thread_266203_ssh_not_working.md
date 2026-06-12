---
title: "ssh not working"
date: 2006-09-26
forum: Desktop Environments
---

### Post by compudude86 on 2006-09-26
hi all,
i do not know what is wrong, i have installed the ssh server on an almost exactly similar ubuntu setup i have at work, but for some reason, ssh loads and says [ ok ], but i cannot ssh into it. i can ssh into all my other computers on my network, but for some odd reason its not working. i also had to uninstall and reinstall a few times for it to work. i must also state that i could ssh localhost with no problems. any ideas?

---

### Post by jISh on 2006-09-26
What happens when you try to login? Connection refused, or something deeper than that?

---

### Post by compudude86 on 2006-09-26
im using putty and it says "network error. connection refused." i just added above i can ssh by localhost with no problem

---

### Post by Mr Frosti on 2006-09-26
The "ssh" utility that you are using does not include the server by default. You can SSH out, but no computers can SSH into your machine. This can be resolved by installing the "sshd" packages from Synaptic. 

This will also provide SFTP, and SCP

---

### Post by compudude86 on 2006-09-27
i just ssh'ed in using the loopback address. i installed from synaptic already.

---

### Post by compudude86 on 2006-09-27
my synaptic shows no sshd package

---

### Post by x64Jimbo on 2006-09-27
got a firewall like firestarter? you might want to create an "allow" rule for the SSH port 22

---

### Post by compudude86 on 2006-09-27
i have a freesco firewall on a seperate machine, but the thing is i can still access my other systems, just not the ubuntu. is there some kind of block file in ubuntu?

---

### Post by x64Jimbo on 2006-09-27
check if you have firestarter - that's a common ubuntu firewall

---

### Post by compudude86 on 2006-09-27
nope, this is stock off the newest cd image, and running apt-get remove firestarter yields nothing

---

### Post by jmartini on 2006-09-27
First check to see if sshd is actually listening to a port other than localhost:

```
jmartini@zen:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...                             [ ok ]
jmartini@zen:~$ netstat -lt | grep ssh
tcp6       0      0 *:ssh                   *:*                     LISTEN
```

If you're listening on the ssh port on more than just localhost then you may have a firewall problem.  If you're only listening to the localhost interface you'll need to edit /etc/ssh/sshd_config and set the ListenAddress appropriately:

```
jmartini@zen:/var/log$ head /etc/ssh/sshd_config
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
```

---

### Post by compudude86 on 2006-09-27
well duuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuh to me, i was going with my puttys default port of 24, but running it with port 22 got me in, thanks

---

### Post by dweez on 2006-11-08
Look for openssh-server and install that for the sshd package.

---

