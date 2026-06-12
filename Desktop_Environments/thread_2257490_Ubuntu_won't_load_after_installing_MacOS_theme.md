---
title: "Ubuntu won't load after installing MacOS theme"
date: 2014-12-20
forum: Desktop Environments
---

### Post by Ivan_Dumancic on 2014-12-20
Hello!
I have a question.
I tried to flash MacOS based theme for my Ubuntu 14.04 LTS, and after rebooting I just got a black screen with mouse indicator in the middle.
I can enter GRUB mode but I don't know what to do there. Can you help me?
Thanks in advance! :)

---

### Post by Frogs Hair on 2014-12-20
Hello and Welcome 

> I tried to flash MacOS based theme for my Ubuntu 14.04 LTS,


Can you explain futher and link the installed theme ?

---

### Post by Ivan_Dumancic on 2014-12-20
[http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html](http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html)

Here is the tutorial I used.
What I need to explain?
And if this is something that will help you, the GPU is AMD Radeon HD6650M.

---

### Post by Ivan_Dumancic on 2014-12-21
Well, I found out what's causing the problem with the fail booting, it's the LightDM, when I flashed that, then the OS wouldn't boot anymore. Any help?

---

### Post by Frogs Hair on 2014-12-21
What is "flashed" ?

---

### Post by Ivan_Dumancic on 2014-12-21
Installed, sorry for misunderstanding.

---

### Post by Frogs Hair on 2014-12-21
If you installed on 14.04 you could try reverting to the Ubuntu Light DM per the instructions. ```
 [COLOR=#333333][FONT=verdana]sudo apt-get remove mbuntu-lightdm-v3[/FONT][/COLOR]
``` This would have to be done from tty using Ctrl +Alt +F1 then reboot with the following ```
sudo reboot
```

---

### Post by Ivan_Dumancic on 2014-12-26
Well, thank you very much, I done it! Couldn't answer earlier, I had job to do, so I couldn't work with Ubuntu. Now I can, and I did it. Let's get back to Ubuntu. :D
Thanks !

---

