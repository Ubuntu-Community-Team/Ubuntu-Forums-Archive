---
title: "remote terminal is very slow"
date: 2009-01-01
forum: General Help
---

### Post by minashokry on 2009-01-01
hello,

I am using ssh to open a terminal to a remote server
I am using ubuntu 8.10 amd64 as client and server runs ubuntu 8.10 server

in terminal I type
```
ssh my_user_name@my_server
```

my problems are these
1 - terminal runs very slow (it takes time between pressing a letter and see it on terminal) when opening a remote connection but it works normal on local computer.

2 - pressing arrows doesn't work (for example pressing up doesn't show last executed command and pressing left doesn't go to previous character).

is there something missing or there are some configs I have to make on my computer or on the server?

thanks in advance...

---

### Post by croto on 2009-01-01
Hi,

I think it is just related to the network speed. What is the output of the ping command?
```

ping my_server

```

I expect to see times of the order the delay you are experiencing. There are many factors that can affect network speed. Are you using broadband? Are you using wireless?, maybe the wireless connection is not good. Are you using any P2P program?, maybe that is saturating the network.

---

### Post by minashokry on 2009-05-25
thanks for reply but I don't think it is a network problem.
when I switch user to root, speed is better and other keys (up and left) works. but of course working as root isn't safe. is it a missing configuration file in my home at server?

---

