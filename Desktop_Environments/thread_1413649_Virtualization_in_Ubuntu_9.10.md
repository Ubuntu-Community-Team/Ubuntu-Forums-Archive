---
title: "Virtualization in Ubuntu 9.10"
date: 2010-02-22
forum: Desktop Environments
---

### Post by cbaron0185 on 2010-02-22
Hello everyone, 

I just ordered a laptop, if any of you follow woot.com it was ordered from there ( [http://www.woot.com/Blog/ViewEntry.aspx?Id=11564](http://www.woot.com/Blog/ViewEntry.aspx?Id=11564) ) 

Anyway, I want to have Ubuntu 9.10 running as my primary OS and Windows 7 Virtualized for gaming and Windows needs. I have used VMware in the past which is okay for server end needs. I have not really used Virtual Box too much. What I am concerned is if any of these programs will be able to take advantage of my hardware acceleration. 

I also know wine is out there and I wouldn't have the overhead of a full OS. If anyone has ideas I would be glad to hear them. In the mean time I guess I will keep looking, while I wait for the laptop to come in. 

Thanks again!

---

### Post by cbaron0185 on 2010-02-22
I found this post [http://ubuntuforums.org/showthread.php?t=716713](http://ubuntuforums.org/showthread.php?t=716713) that does help significantly. If anyone has other options let me know. 

Thanks again!

---

### Post by Jeff Anthony on 2010-02-23
I would strongly suggest VirtualBox for your particular needs. It is capable of exactly what you are looking for, has a decent GUI, and the seamless mode is really slick.

I might even suggest keeping your Windows 7 on the bare-metal for your extreme gaming needs. Use Wubi to get Ubuntu on the boot list. After setting Ubuntu as the default OS use VirtualBox seamless Windows VM for your 'lighter' Windows apps.

---

### Post by the yawner on 2010-02-23
Afaik, gaming is still a miss with a virtual Windows environment. You're better off dual booting.

---

### Post by claracc on 2010-02-23
I also think the best option is to have a dual boot windows 7/ubuntu karmic koala and use the windows partition to play videogames.

---

### Post by Hero of Time on 2010-02-23
I recommended the suggested two comments above. VirtualBox does have 3D options, it is nowhere near as fast as native. Hardware acceleration is not as advanced as you may think, it uses the Wine 3D project for it's 3D features. You're better of with Wine itself than run games through a VM. Of course, native Windows beats Wine.

For dual boot, you can happily install Windows first and then use the normal installer for Linux. Wubi is nice, for people who have no idea how things work. Native install gives it a partition on it's own to work with, with the Grub boot loader and allows you to boot your system to Linux if Windows breaks (including it's boot loader).

---

### Post by shihkster1015 on 2010-02-23
If you want the speed and a fast gui, you're better off dualbooting
If you want to use like office applications or photo editing or anything that doesn't require a fast framerate, then you should go ahead and use a virtualization program.

---

### Post by cbaron0185 on 2010-02-23
Thanks guys this helps a lot, I have been using Ubuntu for my server needs. I was really unsure how far the graphic emulation has come over the past few years.

I will move forward with doing a dual boot, seems the best way to go. 

Thanks again

---

