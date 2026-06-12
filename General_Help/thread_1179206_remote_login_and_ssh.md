---
title: "remote login and ssh?"
date: 2009-06-05
forum: General Help
---

### Post by abhilashm86 on 2009-06-05
i'd like to know more things about seting and using ssh, basically i don't know anything except it can do remote login, so where can i get information about how to install and use that stuff and play around,

i watched a video which used ssh and did something on server,so.......

---

### Post by mixmaster on 2009-06-05
This should get you started 

[http://lmgtfy.com/?q=ssh+setup](http://lmgtfy.com/?q=ssh+setup)

---

### Post by Boondoklife on 2009-06-05
The easiest way would be to take a look at the ssh man page, If you look through the options it will give you a good idea of what you can do. But here are just a few.


[LIST]
[*]Allows for remote administration of server
[*]Allows you to bounce your connection inside the network
[*]Allows you to forward your connection and other local ports to another machine inside the network with out needing to setup more port forwarding on the router
[/LIST]
There are lots more

---

### Post by ARhere on 2009-06-05
A quick tip for you.

When logging into a computer using ssh, always use...

```
ssh <user>@<IP or domain name>
```

if you just "ssh <server name>" then it tries to log in as the user name of the current machine you are using.

Also, remember you can use ssh for file transfer as well, but I find it easier to use a GUI tool for this.  There is also an ssh client/server compiled for Windows command line as well.  Very useful!

-AR

---

