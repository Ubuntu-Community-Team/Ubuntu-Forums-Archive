---
title: "Packages missing on install"
date: 2005-07-31
forum: Desktop Environments
---

### Post by gordonbp on 2005-07-31
This site, [http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/) tells me I should have Thunderbird and Pan installed as default. there's no trace of them anywhere. Nothing in any menu, nor can I run them from a terminal. What's going on?

---

### Post by heimo on 2005-07-31
It's not a list of packages that are installed by default. Use sypaptic (System->Administration->Synaptic Package Manager) to install software. Refer to  [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) for information on how to add repositories to /etc/apt/sources.list

---

### Post by gordonbp on 2005-07-31
[QUOTE=heimo]It's not a list of packages that are installed by default. Use sypaptic (System->Administration->Synaptic Package Manager) to install software. Refer to  [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) for information on how to add repositories to /etc/apt/sources.list[/QUOTE]
 Thanks - that's got me Thunderbird, but still no trace of Pan. I'll have to get it the same way I got it for Fedora Core 4!

---

### Post by heimo on 2005-07-31
It's in main repository. I would try another mirror (change /etc/apt/sources.list). Or run sudo apt-setup and choose something else you chose earlier. For me, Finnish mirrors don't work, for Hoary I use Swedish mirrors and for Breezy US-mirrors.

---

### Post by gordonbp on 2005-07-31
[QUOTE=heimo]It's in main repository. I would try another mirror (change /etc/apt/sources.list). Or run sudo apt-setup and choose something else you chose earlier. For me, Finnish mirrors don't work, for Hoary I use Swedish mirrors and for Breezy US-mirrors.[/QUOTE]
 Unfortunately this is the type of error message I have got all the time when trying to update:

Testing apt sources...
0% [Connecting to us.archive.ubuntu.com (1.0.0.0)]
ERR: time out. Cannot connect.

It doesn't matter WHAT source I try to use, I get this EVERY time. (I'm on ADSL........)

---

### Post by heimo on 2005-07-31
You have some kind of network problem... do you use proxy to access internet? Have you tried changing from http to ftp archives? If you type dig us.archive.ubuntu.com does it resolve? (give you a valid ip address?) Can you ping that ip? Does your internet connection work with browser? Go to 
[http://us.archive.ubuntu.com/ubuntu/pool/main/p/pan/](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pan/)
do you see a list of deb packages?

:) That's the chain of questions I'd go through.

---

### Post by Xian on 2005-07-31
[QUOTE=gordonbp]Unfortunately this is the type of error message I have got all the time when trying to update:

Testing apt sources...
0% [Connecting to us.archive.ubuntu.com (1.0.0.0)]
ERR: time out. Cannot connect.

It doesn't matter WHAT source I try to use, I get this EVERY time. (I'm on ADSL........)[/QUOTE]
Read this [THREAD](http://www.ubuntuforums.org/showthread.php?p=224019&#post224019) for possible solution.

---

### Post by gordonbp on 2005-07-31
[QUOTE=heimo]You have some kind of network problem... do you use proxy to access internet? Have you tried changing from http to ftp archives? If you type dig us.archive.ubuntu.com does it resolve? (give you a valid ip address?) Can you ping that ip? Does your internet connection work with browser? Go to 
[http://us.archive.ubuntu.com/ubuntu/pool/main/p/pan/](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pan/)
do you see a list of deb packages?

:) That's the chain of questions I'd go through.[/QUOTE]
 dig us.archive.ubuntu.com resolves, and I can ping the ip address. I'm posting all these posts from my own browser on Hoary. If I go here: [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pan/](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pan/)
I certainly see a list of packages!

---

### Post by gordonbp on 2005-07-31
[QUOTE=Xian]Read this [THREAD](http://www.ubuntuforums.org/showthread.php?p=224019&#post224019) for possible solution.[/QUOTE]
 Thanks for that link - I had a look there. My network card is currently set up for DHCP. I changed  to a static IP - 192.168.1.5 with the normal subnet mask and a gateway of 192.168.1.1. (The router is supplied pre-configured by my Wife's company who also pay the ADSL costs <VBG> but that means I can't access the router) Having done that, I couldn't access the internet at all.

---

### Post by gordonbp on 2005-07-31
[QUOTE=Xian]Read this [THREAD](http://www.ubuntuforums.org/showthread.php?p=224019&#post224019) for possible solution.[/QUOTE]
 Bingo. Went to the ISP site, put it's dns server in resolv.conf and all seems to be OK!

Many thanks for your help guys.

---

### Post by Xian on 2005-07-31
[QUOTE=gordonbp]Bingo. Went to the ISP site, put it's dns server in resolv.conf and all seems to be OK![/QUOTE]
I have to say that is an odd thing to find and not be more documented.
To be honest, I don't even know why I was reading that thread. :)

---

### Post by gordonbp on 2005-08-01
[QUOTE=Xian]I have to say that is an odd thing to find and not be more documented.
To be honest, I don't even know why I was reading that thread. :)[/QUOTE]
 I've now filed a bug report because after having saved the resolv.conf file, when I turn my machine on the next time, the file has reverted to it's previous content! Very exasperating, as it means the file has to be edited for every session where I might be expected to do updates!

---

### Post by heimo on 2005-08-01
Out of curiosity, do you use DHCP or manual network configuration? If you run sudo dhclient eth0, does it mess up your resolv.conf settings?

---

