---
title: "Re: Network Browsing in IceWM"
date: 2007-11-19
forum: Desktop Environments
---

### Post by BLTicklemonster on 2007-11-19
Aysiu, how does one browse a network in Icewm? Not that mine works, but if I ever get it going (2 years in Ubuntu, and still no network) I'd like to know how to do it.

---

### Post by aysiu on 2007-11-19
I usually use Nautilus: ```
nautilus --no-desktop
``` I know there are ways to use *smbclient* as well, but I prefer Nautilus.

---

### Post by BLTicklemonster on 2007-11-19
Oh, okay, I can do that. Now to see if I can ever get samba to behave. I came close to walking away from Ubuntu out of sheer frustration, but :) when I started messing around in windows, I hated it! So to heck with it, I'm hanging in there.

Thanks A.

---

### Post by BLTicklemonster on 2007-11-20
Um, in startup?

---

### Post by ghandi69_ on 2007-11-20
BLT ticklemonster, 

I dont know about you, but I had a lot of problems getting Samba setup, however, recently, I do have a home server running Ubuntu that runs samba, and is currently acting as a file server for 4 XP computers and 2 Ubuntu computers, and it works flawlessly.

I would take a look at my smb.conf file, and make sure all all of your machines are on the same domain/workgroup, and give it another go, I really was just one step away like the whole time!> [global]
    workgroup = LINUX
    security = user
    wins support = yes
    log level = 1 
    max log size = 1000
    read only = no
[MyFiles]
    browsable = yes
    read only = no
    path = /		


Note, for me at least, the 'user' needed to be a user on created on the server machine, so you need to create the user account normally and then use 'smbpasswd -a' , which adds the account to the Samba user database and then sets the password for it. I created a blank password, so when my XP using roommate browse the files, they just have to enter the correct username

---

### Post by BLTicklemonster on 2007-11-20
Thanks, Ghandi, but I've had it going without wins before. I just don't understand how I can follow the foolproof video on youtube that everyone rants about on a fresh install, and still not be able to use the network. Suddenly, I can't even see the XP boxes anymore. I'm asked for a password to login with! What's up with that? Is there any way to remove all the users and passwords and start over?

---

### Post by TeaSwigger on 2007-11-21
Oh for browsing shares there are a few GUIs in the repos - if you don't want to drag in Nautilus, they'd work. You find the share and mount it in the app. Also KDE has alternative of its own like the zeroconf using a smb:/ protocol to nav the network and use available shares without having to mount any. Pretty cool. In Fluxbox or IceWM though I mount 'em so I don't need Nautilus or Konqueror or what not, any file manager will do. I just use a light file manager for keeping resource use lighter.

> **BLTicklemonster said:**
> Thanks, Ghandi, but I've had it going without wins before. I just don't understand how I can follow the foolproof video on youtube that everyone rants about on a fresh install, and still not be able to use the network. Suddenly, I can't even see the XP boxes anymore. I'm asked for a password to login with! What's up with that? Is there any way to remove all the users and passwords and start over?

Tell me about it. The trouble I had! :mad:

What I did to succeed - I think, I'm a bit hazy about the whole mess - was follow these:
Stormbringer's HowTo
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
for setting up and
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
(using .smbcredentials) to mount the shares in my linux box.

Oh in this bit:

```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```

...the first time I made the mistake of dropping both in the term. Ya have to be sure you do the -a first, then do the -e for each entered. You'd probably figure it right but thought I'd mention it in case. I can't tell ya how many times I had to pour over those things either. Gah. Good luck to you!

---

### Post by BLTicklemonster on 2007-11-21
Thanks TeaSwigger, I'll try that, too. 

(gets forklift to drag out log on "networking in linux" i'm keeping)

---

