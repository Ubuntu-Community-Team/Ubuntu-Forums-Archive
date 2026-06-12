---
title: "Cannot create SSH tunnels on eth1"
date: 2005-12-25
forum: General Help
---

### Post by jonsson on 2005-12-25
I'm currently running Kubuntu breezy but I had the same problem in Horay. I'm guessing it's a simple configuration issue.

My laptop has a built in ethernet interface (eth0) and a PCMCIA wifi card that I plug in when I need it (eth1). When I have a eth0 connected to a cable, I can do 

```
$ ssh -L 10143:localhost:143 user@remote.host
```

to set up a tunnel to my mail server. However, if I am connected through eht1 instead, I get

"bind: Cannot assign requested address"

Any ideas as to where I should begin to look for a problem?

---

### Post by gsdefender on 2005-12-25
I don't know if I have correctly understood your question; it seems to me that the problem lies in eth0 being the default route, and packets are trying to get through it by default. Have you tried to put the address binded to eth1 before the first [port]?

---

### Post by jonsson on 2005-12-25
Progress :-) That seems to work. However, I now have to connect to my local IP and not to "localhost" which was more convenient.

---

### Post by jonsson on 2006-04-30
I got a private message with another solution. If I first do:

```
sudo ifdown lo
sudo ifup lo
```

it works just like when I'm plugged in. :-D

---

