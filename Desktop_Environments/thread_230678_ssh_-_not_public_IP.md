---
title: "ssh - not public IP"
date: 2006-08-06
forum: Desktop Environments
---

### Post by matko on 2006-08-06
hello.

i would like to know how can i connect from external network to
mu friends pc.

he has not public IP. i know IP of his ISP and also his internal ip.

how can i cinnect to him with ssh ?

thanx

---

### Post by lamego on 2006-08-06
If he doesn't have a public IP he is not connected to the internet and you can't connect to him,
If he uses some kind of modem or router to share the network he must setup port fordwarind on the router to redirect the ssh connections to the internal ssh server.

---

### Post by pdub on 2006-08-06
I will assume that your friend has a router/firewall that connects to his ISP on the outside and to his computer on the inside.

You will need to port forward TCP 22 in the router/firewall to his internal IP address.

Have your friend check to ensure ssh is installed on his PC as follows:

ssh localhost

He should get something like this:

pdub@pdub-home:~$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX.
Are you sure you want to continue connecting (yes/no)?

Remember to use strong passwords and you may also wish to consider reading this article to improve the securing of ssh.

[http://geekpit.blogspot.com/2006/04/five-minutes-to-more-secure-ssh.html](http://geekpit.blogspot.com/2006/04/five-minutes-to-more-secure-ssh.html)

---

### Post by matko on 2006-08-06
thanks will try port forwarding.

about the security is fine site. but i dint use key auth....

because i have stable IP i restricted connection in /etc/hosts.deny

```
sshd: ALL EXCEPT 85.216.0.0
```

is it safe or hijacker can bypass this hosts.deny ?

what is funny is that when i ssh mi friends ISP it answered and asked for password. that mean ISP have lack of security and everybody can bruteforce their ssh. lol

---

