---
title: "Ubuntu 11.10 Remote Desktop to Windows 7 Doesn't work"
date: 2011-12-07
forum: Desktop Environments
---

### Post by jaime256 on 2011-12-07
So I've been trying to connect to my Windows 7 Pro box for over a week and have had no luck. I was able to connect to my box before installing this version on my desktop. So far I have tried remmina, remoted desktop viewer, KRDC and I'm still having no luck. I can ping the machine, but just can't get a remote desktop connection to it. I manage that machine from the desktop since it's the htpc and don't want to be in front of the TV every time I need to change something. Has anyone found a fix for this on this version of Ubuntu? Thanks.

Note: I should mention I'm using the gnone shell and classic mode.

---

### Post by cybergalvez on 2011-12-07
are you getting any error messages? can you run one of the RDP clients in a terminal window to see if there is an error

---

### Post by oldtimer7777 on 2011-12-07
This is what I use to remote connect to Windows 7:

[https://debianhelp.wordpress.com/2011/07/05/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/](https://debianhelp.wordpress.com/2011/07/05/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/)

Never any issues or problems either. 

> **jaime256 said:**
> So I've been trying to connect to my Windows 7 Pro box for over a week and have had no luck. I was able to connect to my box before installing this version on my desktop. So far I have tried remmina, remoted desktop viewer, KRDC and I'm still having no luck. I can ping the machine, but just can't get a remote desktop connection to it. I manage that machine from the desktop since it's the htpc and don't want to be in front of the TV every time I need to change something. Has anyone found a fix for this on this version of Ubuntu? Thanks.

Note: I should mention I'm using the gnone shell and classic mode.

---

### Post by jaime256 on 2011-12-07
No errors show up just a blank screen when running the programs. They just stay blank.

> **cybergalvez said:**
> are you getting any error messages? can you run one of the RDP clients in a terminal window to see if there is an error

---

### Post by jaime256 on 2011-12-07
Thanks, I know about that program, I'm just trying to get these working without having to install too many programs.

> **oldtimer7777 said:**
> This is what I use to remote connect to Windows 7:

[https://debianhelp.wordpress.com/2011/07/05/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/](https://debianhelp.wordpress.com/2011/07/05/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/)

Never any issues or problems either.

---

### Post by jaime256 on 2011-12-07
I'm currently restoring my old windows on my laptop now. I never did use it, but now I think the updates should make it work nicer so I'm going back to that one for now. Once it's done I'll double check from there and see if I can log in to my 7 box. So now I'm down to just one Ubuntu box which is the desktop I'm using.

---

### Post by thaelim on 2011-12-07
Your problem is caused by the higher level of security enabled by default for Remote Desktop in Windows Vista onwards. You need to reconfigure your Windows machine to disable NLA so that Linux RDP clients can connect to it. On the windows machine:

- Start -> type "remote"
- Select "Allow remote access to your computer"
- In the resulting dialog select "Allow remote access from computers running any version of Remote Desktop (less secure)". Click OK
- Done

---

### Post by jaime256 on 2011-12-07
Thanks thaelem. You're half right. I had set this up already, but I don't know what update or if adding a vpn connection reset this setting to not allow connections. I just tried my laptop and got the same thing so that's when I went back to the htpc and see what the hell happened. In short, this was reset back to "do not allow any connections" and I just chose the "allow" again and things are back up. Hope this helps others scratching their heads on this. Thanks for the input guys. So all the programs are now connecting fine. Phew...weird but that's what happened, still testing Windows 7 with Ubuntu and XP.



> **thaelim said:**
> Your problem is caused by the higher level of security enabled by default for Remote Desktop in Windows Vista onwards. You need to reconfigure your Windows machine to disable NLA so that Linux RDP clients can connect to it. On the windows machine:

- Start -> type "remote"
- Select "Allow remote access to your computer"
- In the resulting dialog select "Allow remote access from computers running any version of Remote Desktop (less secure)". Click OK
- Done

---

### Post by jaime256 on 2011-12-07
Now I have a question about the ubuntu programs, do they support Network Level Authentication? I just updated the xp client and want to know if Ubuntu clients support this. I suppose I'll find out when I try it, but just thought I ask since I haven't yet.

Well, I just answered my own question, they don't. I guess this is a windows support task, if not how can this be added to the Ubuntu clients?

So far all xp to windows 7 are up and running, including vpn, I know this isn't a windows thread/site, but just thought I mention it while testing all three system connections.

---

### Post by jaime256 on 2011-12-09
I found the answer to my last question about network level authentication here. So in short, you can't use level authentication with ubuntu since that's a windows feature.
[http://blogs.technet.com/b/askperf/archive/2008/02/16/ws2008-network-level-authentication-and-encryption.aspx](http://blogs.technet.com/b/askperf/archive/2008/02/16/ws2008-network-level-authentication-and-encryption.aspx)

---

