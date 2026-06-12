---
title: "Help me with Linux"
date: 2005-12-17
forum: Desktop Environments
---

### Post by mailviruskid on 2005-12-17
Dear Any One Who can help,

I am a first time linux user and i need help with two things:
1) i need help with using the internet on my linux computer i have yahoo dsl sbc.
2) i need help with checking my ethernet card because it does not know how to see it.
The reason why i start to use linux is because is it is so much better than microsoft. If i get linux to work on my first computer then i will put it on all of my computers.

Can you please show me how to do it step by step please. I have yahoo dsl. The Ubuntu is the name of the linux that I am using.  The computer is an IBM Pentium III with a 20G Hard drive with a  256 MB of ram.  I have been do my research for 10 days. PLEASE. THANK YOU.

CAN YOU PLEASE HELP ME!
 
Thank you,
Taqi Jaffery

---

### Post by aysiu on 2005-12-17
I'm using Yahoo! DSL as well. I didn't have to do anything. Ubuntu just auto-detected my ethernet connection.

It probably has very little do with Yahoo! and a lot to do with your ethernet card. By the way, are you using Kubuntu or Ubuntu? I don't know because you've double-posted ([another one in the Ubuntu section](http://www.ubuntuforums.org/showthread.php?p=583904)).

---

### Post by HermanAB on 2005-12-17
There are a couple of utilities that you need to know in order to fix network problems:
ifconfig
ping

Read the man pages, run them, play with them and be happy!

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by jejones3141 on 2005-12-17
[QUOTE=mailviruskid]
Can you please show me how to do it step by step please. I have yahoo dsl. The Ubuntu is the name of the linux that I am using.  The computer is an IBM Pentium III with a 20G Hard drive with a  256 MB of ram.  I have been do my research for 10 days. PLEASE. THANK YOU.[/QUOTE]

If, when you installed Ubuntu, you told it to use DHCP for networking, it should just work. OTOH, if you didn't have DSL at the time, it might have decided not to start ethernet by default. In that case, click System>Administration>Networking and tell it to enable what it probably calls eth0, and use DHCP.

---

