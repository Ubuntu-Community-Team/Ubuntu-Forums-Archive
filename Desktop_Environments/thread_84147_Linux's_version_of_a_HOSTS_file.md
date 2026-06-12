---
title: "Linux's version of a HOSTS file?"
date: 2005-10-30
forum: Desktop Environments
---

### Post by jimmygoon on 2005-10-30
I would like linux to address the domain: [http://www.jimmygoon.com](http://www.jimmygoon.com) as [http://127.0.0.1](http://127.0.0.1)

ie: when  I type jimmygoon.com in browser have it goto 127.0.0.1 instead.

I'm testing a bunch of stuff for a website I'm designing.

can anyone help me with this? thanks

---

### Post by Xian on 2005-10-30
Yeah, the file is basically the same.
Goto /etc/hosts

Edit as desired.

---

### Post by jimmygoon on 2005-10-30
[QUOTE=Xian]Yeah, the file is basically the same.
Goto /etc/hosts

Edit as desired.[/QUOTE]

you sir are a god send. thank you. and thanks to the amazing linux community

edit: can you tell me what I need to add to it to achieve my desired effect. lol. I'm confused by the file.

---

### Post by stoeptegel on 2005-10-30
It's the same file, but in contrast to the w32 version of hosts, the linux version is not empty: it as some lines in it you may not want to delete because your internet will stop working.

---

### Post by jimmygoon on 2005-10-30
[QUOTE=stoeptegel]It's the same file, but in contrast to the w32 version of hosts, the linux version is not empty: it as some lines in it you may not want to delete because your internet will stop working.[/QUOTE]


nah. I got it. I just needed to add jimmygoon.com and [www.jimmygoon.com](www.jimmygoon.com) to the line beginning with 127.0.0.1

I don't have any ipv6 around here anyways so its not important and theres nothing else in the host file to worry about. 

thanks guys. I got it now ;)

---

