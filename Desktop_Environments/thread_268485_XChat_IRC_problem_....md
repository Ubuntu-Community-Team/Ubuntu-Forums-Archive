---
title: "XChat IRC problem ..."
date: 2006-09-30
forum: Desktop Environments
---

### Post by dbee on 2006-09-30
So my xchat won't connect to any of the irc servers ... I don't know what's wrong. My internet works fine though ... :-(
> 
* Looking up ircnet.hinet.hr
* Looking up Hostname: 127.0.0.1
* Unknown host. Maybe you misspelled it?
 Cycling to next server in IRCNet...
* Disconnected ().
* Looking up irc.datacomm.ch
* Looking up Hostname: 127.0.0.1
* Unknown host. Maybe you misspelled it?
 Cycling to next server in IRCNet...
* Disconnected ().
* Looking up ircnet.kaptech.fr
* Looking up Hostname: 127.0.0.1
* Unknown host. Maybe you misspelled it?
 Cycling to next server in IRCNet...
* Disconnected ()

... this just goes on and on. Same thing for freenode or any of the others that I've tried. I've looked in /etc/hosts ... doesn't seem to be a problem. I've also tried to connect via IP address, it still seems to try to resolve 127.0.0.1.

Anyone got any ideas here ?

Thanks

---

### Post by henriquemaia on 2006-09-30
127.0.0.1 is the same as localhost, or your own computer. He's not connecting to any server because it isn't connecting to the internet.


["What is 127.0.0.1?]("http://www.tech-faq.com/127.0.0.1.shtml")    [127.0.0.1 is the standard IP address used for a loopback network connection.]("http://www.tech-faq.com/127.0.0.1.shtml")
  
[This means that if you try to connect to 127.0.0.1, you are immediately *looped back* to your own machine.]("http://www.tech-faq.com/127.0.0.1.shtml")
  [If you telnet, ftp, etc...  to 127.0.0.1, you are connected to your own machine.]("http://www.tech-faq.com/127.0.0.1.shtml")
  [In other words, 127.0.0.1 is **you**."]("http://www.tech-faq.com/127.0.0.1.shtml")

---

### Post by dbee on 2006-09-30
Ah, yes thanks. I'm aware that 127.0.0.1 is the same as localhost. What I'm not aware of however is why xchat tries to connect with all the IRC servers at this address ...

Anyone have any ideas ... ?

---

### Post by henriquemaia on 2006-10-01
Does it happens with if you use xchat as another user?

---

