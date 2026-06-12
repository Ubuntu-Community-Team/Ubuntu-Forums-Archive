---
title: "Access folder over the internet =)"
date: 2009-04-18
forum: General Help
---

### Post by johannes_h on 2009-04-18
Hi !
I have both a desktop and laptop running ubuntu. From my laptop, can I access certain folders on my desktop, just as a usb-drive or cd? I'd like to have access to some folders on my desktop, from my laptop, just as other folders on my laptop. No ftp.. 

Can anyone tell me what to look into, it would have to work over internet :)

Thanks!

---

### Post by SkippoGuangiacomo on 2009-04-18
What about sharing the folder in the network? Would that fit you? Follow this tread:

[http://ubuntuforums.org/showthread.php?t=1121087&highlight=sharing+network+folder](http://ubuntuforums.org/showthread.php?t=1121087&highlight=sharing+network+folder)

---

### Post by Svensk023 on 2009-04-18
Yes, you want SSH, it is perfect for remotely getting into your desktop from a laptop.

this link should help you

[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by johannes_h on 2009-04-18
> **Svensk023 said:**
> Yes, you want SSH, it is perfect for remotely getting into your desktop from a laptop.

this link should help you

[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

I'll have a look at that, thanks :)

---

### Post by johannes_h on 2009-04-18
> **SkippoGuangiacomo said:**
> What about sharing the folder in the network? Would that fit you? Follow this tread:

[http://ubuntuforums.org/showthread.php?t=1121087&highlight=sharing+network+folder](http://ubuntuforums.org/showthread.php?t=1121087&highlight=sharing+network+folder)

That I already know how to.. I want to share over internet, not just LAN ;) Thanks anyway

---

### Post by johannes_h on 2009-04-18
Isn't there anything else? With SSH I have to install putty on a windows machine :P Of course no big deal.. But I know it should be possible from my computer in windows to click on "connect to network station" or something like that, and very simply get access to certain folders..

---

### Post by johannes_h on 2009-04-18
Samba did the trick ;)

---

