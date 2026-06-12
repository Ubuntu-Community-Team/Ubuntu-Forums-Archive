---
title: "can't boot to windows xp"
date: 2011-02-14
forum: Desktop Environments
---

### Post by sharathk on 2011-02-14
had installed ubuntu alongside windows xp in dual boot. everything was working fine untill last week. 

last week i did share a folder on NTFS partition from ubuntu to be accessed by my laptop which runs XP. i could access the folder after i ran this command from terminal "sudo smbpasswd -a myusername". After this i cannot boot to windows. it shows up windows screen and reboots again.  ubuntu works fine. what do i do to get back windows XP to working again?

---

### Post by sharathk on 2011-02-15
i have the windows xp disk clone before ubuntu was installed. if i restore it will it change the boot menu? if yes can i get back/create the boot menu to dual boot with ubuntu?

i also do have xp restore cd, can i just try to repair xp instead?

anyone?

---

### Post by Krytarik on 2011-02-16
First try to repair the Windows boot by using your Recovery CD. It will most probably remove the Grub boot menu. But is should be fairly easy to re-install, by using a Live/Install-CD of Ubuntu:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

And sorry for the delay, I subscribed to your thread before, but I don't know what may have caused your boot issue. But if Grub manages to initiate the Windows startup, like you said, then it's apparently an issue of Windows itself. I looked up the command you mentioned, and it seems not possible, that it has caused your issue.

---

### Post by sharathk on 2011-02-16
Thanks for the response. i'll try to repair XP and will post how that goes.

---

### Post by sharathk on 2011-02-24
Thanks that helped. i did replace the grub from live cd after reinstalling windows xp clone and dual boot is working fine now.
i found another page which was a little simpler:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

thanks again

---

### Post by Krytarik on 2011-02-24
> **sharathk said:**
> Thanks that helped. i did replace the grub from live cd after reinstalling windows xp clone and dual boot is working fine now.
i found another page which was a little simpler:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

thanks again
Glad that you managed it. Yeah, aside from the fact that the same commands get used, those one is a bit more demonstrative. Actually I found that I already have it in my bookmarks also.:P

---

