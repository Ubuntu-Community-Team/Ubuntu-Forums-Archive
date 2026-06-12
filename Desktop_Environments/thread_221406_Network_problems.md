---
title: "Network problems"
date: 2006-07-23
forum: Desktop Environments
---

### Post by orengabay on 2006-07-23
Hi All,
I am new with Ubuntu but I finally managed to do the move from windows and now this is my main OS.

Still I have a annoying network problem that I need help with.

For example: when I install software using apt-get or Synaptic it can't access the server: archive.ubuntu.com and I get error. So I open a command line window and ping the server: archive.ubuntu.com and then it works.
The same problem happens with all the tools that needs to access network services: php pear and more.

My environment is: Ubuntu 6.0.6 
Hardware: HP Pavilion DV 1000 with built in wireless.
Connect to the Internet using a home wireless network.

Thanks,
Oren

---

### Post by scxtt on 2006-07-23
some of the archive servers have been having problems - and if it's in california, there have been power problems that have 'hurt' many hosts on the west coast (myspace, yahoo) ...

are you saying that just the ping works or after a successful ping you can then **sudo apt-get update** fine?

---

### Post by orengabay on 2006-07-24
Yes, Only after a successful ping apt-get works fine. It look as if it "initialize" the connection to this address. 
It is important to note that it is exactly the same with other programs.
Thanks,
Oren

---

