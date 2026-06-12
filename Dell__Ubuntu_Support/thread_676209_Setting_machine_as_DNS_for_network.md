---
title: "Setting machine as DNS for network"
date: 2008-01-23
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2008-01-23
Hello,
Can anyone help me set up DNS?  I have a Dell XPS using Fiesty (704) and I want to set it up so my network can point to it as the DNS.  Thank you.  

*I am a newbie to this.  Thanks.  -aw

---

### Post by Monkey_Tales on 2008-01-24
[http://www.opendns.com/](http://www.opendns.com/)

:popcorn:

---

### Post by arvadawest on 2008-01-27
Hi Thank you.  I see OpenDNS as all my machines pointing to their DNS servers, *but,* I want to set my Ubuntu Linux machine (fiesty) to be the DNS server that my pc's point to.  I currently use Windows 2000 Server as my DNS, but I want to get away from using this and using my Linux machine as the DNS.  Thank  you.  -aw

---

### Post by p_quarles on 2008-01-28
This might help:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

### Post by arvadawest on 2008-01-28
> **p_quarles said:**
> This might help:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

Thank you P_Quarles.  I realize this is "line commands" but is there a way to make my Ubuntu pc in a DNS Server by point and click?  I am sorry if this seems a dumb question.  I am a newbie and used to a Windows environment.  Thank you.  -AW

---

### Post by Monkey_Tales on 2008-01-31
hello again,
try Gbindadmin, this is no command line tool

sudo apt-get install gbindadmin

This program installs under your system menu

have fun):P

---

### Post by Monkey_Tales on 2008-02-01
Hello, 
i forgot to mention this how to set up and configure a dns server in ubuntu

[http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html](http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html)

have fun

:popcorn:

---

### Post by arvadawest on 2008-02-01
> **Monkey_Tales said:**
> Hello, 
i forgot to mention this how to set up and configure a dns server in ubuntu

[http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html](http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html)

have fun

:popcorn:

Hi Monkey_T,
Thanks so much for this.  I will give it a try.  I just hope all my pc's on the network will be able to see it.  Thanks!  -aw

---

### Post by EmoDx on 2008-02-05
> **Monkey_Tales said:**
> Hello, 
i forgot to mention this how to set up and configure a dns server in ubuntu

[http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html](http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html)

have fun

:popcorn:

So do I have to instal bind9 prior to installing gbindadmin? And if so, do I still have to type all the command lines, or is that what gbaindadmin does all wrapped up in a nice GUI? TIA,

-Emo

---

### Post by EmoDx on 2008-02-05
Okie dokie, I have Bind9 installed and gbindadmin installed. When I click on K->System->gbindadmin the app doesn't load. Also, I have gbindadmin listed under my settings menu. Same thing when I click that, it doesn't open the program. Any ideas on what I am doing wrong?

---

### Post by mmichalik on 2008-02-05
EmoDx,  Webmin has a very nice interface to BIND9 that makes things pretty simple.

You can download it from [www.webmin.com](www.webmin.com) and install it on the box that you are going to use for the DNS server.

---

### Post by arvadawest on 2008-03-01
> **mmichalik said:**
> EmoDx,  Webmin has a very nice interface to BIND9 that makes things pretty simple.

You can download it from [www.webmin.com](www.webmin.com) and install it on the box that you are going to use for the DNS server.

Hi,
Do I have to install Bind9 first?  Thanks.  Sorry, I'm a newbie

---

