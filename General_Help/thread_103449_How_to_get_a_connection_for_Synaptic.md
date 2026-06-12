---
title: "How to get a connection for Synaptic ?"
date: 2005-12-14
forum: General Help
---

### Post by Me! on 2005-12-14
I tried to update or connect Synaptic but I did not sucess :( 

How to get a connection for it ?

Internet working fine .
but Synaptic not wrking with the Net , (How to set a username and password for it)

---

### Post by schilcha on 2005-12-14
I'm not really sure, if I understand your problem. 

AFAIK, there's no account for synaptic necessary -- all standard repositories are freely accessible. 
Did you manage to start synaptic?
Did you then get any errors regarding failed connections?
Did you get any other error msgs?

If you're talking about the small box requesting a pwd right after starting synaptic... just enter your own pwd ;)

Good Luck!

---

### Post by Me! on 2005-12-17
thank you for your answer .

Err messeges:
first box :
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)



Second Box(After Download):
[http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://wine.sourceforge.net/apt/binary/Packages.gz:](http://wine.sourceforge.net/apt/binary/Packages.gz:) 407 Proxy authorization required
[http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:) 407 Proxy authorization required
[http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:) 407 Proxy authorization required


_Note that I set the proxy in the settengs->Network_

---

### Post by veehell on 2005-12-20
Hi dudes,
i have one ubuntu at work as testing machine. All been ok. I set the proxy (globaly via gnome tools) it work for few programs, but some Xchat, Irssi and so on needs own. So i take look at the synaptic too. We have 3proxies, covered by one HAA service. So i actually dont know which one is the real one. It does not matter now.
Finally i get the exact machine name, port and have own proxy account.

But synaptic does not work after my test in xchat, irssi and some other programs, even if i specify my favourite proxy.

*There is option in menu, you can ad HTTP,Sock, FTP proxies as well. And here is my point: you have to specify like this*
**<username>:<password>@<proxy.you.hate.net> in next field specify <port>**
Afterward it work perfectly. 

I found few threads here, some guys recommend to use apt-get it self in command line. There are some ways to force the proxy via export http_proxy=<<user>:<pass>@<url>:<port>> and execute apt-get update to get list or error msgs. I tried but without good results (just only few repositories been reached and downloaded indexies) I still dont know why only few and rest said "no proxy auth" . Nevermind. I am glad that Synaptic work with my proxy syntax string. So maybe it help you too.

cheers and Massy X-marry

---

### Post by Me! on 2005-12-24
Thank you 
Thank you Thank you 
Thank you Thank you Thank you 
Thank you Thank you Thank you Thank you 
Thank you Thank you Thank you Thank you 
Thank you Thank you 
Thank you 

it is work fine with your help of :
<b><username>:<password>@<proxy.you.hate.net> in next field specify <port> </b>

Thank you

---

### Post by veehell on 2006-01-26
You are welcome ;)

---

