---
title: "gaming with virtualisation software"
date: 2006-07-18
forum: Gaming &amp; Leisure
---

### Post by el_ricardo on 2006-07-18
I'd like to know how well qemu handles games like half life 2, counterstrike, city of villains etc, i've just got qemu working properly, but i'm worried that CPU guzzling games just won't run on it. would using wine be a better option? If someone could point me towards a **good** guide to set wine up properly that would be good, or just tell me if gaming through qemu is worth trying!

---

### Post by tzulberti on 2006-07-19
You should look at: [http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php), and find the games you play. There should be a lot of info for them.

---

### Post by skirkpatrick on 2006-07-19
The problem with virtualization, like VMWare, is that for some of the peripherals you get a dumbed down, virtual peripheral.  The one that will kill you for games is the video.  You can have the best NVidia or ATI card in your system but your virtual system won't see it, it will only see a very standard video card with little to no 3D capability.

Wine and Cedega, on the other hand, only provide the Windows API and DLLs.  Your game talks directly to the Linux video driver.

---

### Post by KingBahamut on 2006-07-19
[http://www.ubuntuforums.org/showthread.php?t=84344](http://www.ubuntuforums.org/showthread.php?t=84344)

Many features of your video card will not be enabled of course, and I dont know how this will or will not affect gameplay, but Ive heard "stories" of it being successful. 

additional info - 
[http://www.vmware.com/community/thread.jspa;jsessionid=15467EAF94F7EC3E1A979C75FAC2C24D?messageID=204365&#204365](http://www.vmware.com/community/thread.jspa;jsessionid=15467EAF94F7EC3E1A979C75FAC2C24D?messageID=204365&#204365)
[http://www.vmware.com/community/message.jspa?messageID=328070](http://www.vmware.com/community/message.jspa?messageID=328070)

---

