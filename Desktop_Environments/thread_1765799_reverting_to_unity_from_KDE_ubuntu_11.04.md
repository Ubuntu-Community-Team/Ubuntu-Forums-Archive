---
title: "reverting to unity from KDE ubuntu 11.04"
date: 2011-05-23
forum: Desktop Environments
---

### Post by jamie1990 on 2011-05-23
I recently installed KDE via the terminal using _**sudo apt-get install kde-standard**_ and I'm now having difficulty logging in and when I do finally log in all I get is a blank screen, I have tried booting ubuntu in safe mode and uninstalling KDE from the terminal but I am still prompted with the KDE log in screen after rebooting, I was just wondering how to get back to unity.

Any help would be great, many thanks in advance

---

### Post by compmodder26 on 2011-05-23
So, now that you've uninstalled KDE, do you get logged in to the Unity interface when you log in?

If that's the case then to get the Ubuntu log in screen, follow these instructions:

[http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/)

---

### Post by jamie1990 on 2011-05-23
I get the unity pop up notification telling me that I have connected to my WLAN but theres nothing else apart from that, I can get back on to unity but its via the safe mode version, if I run a normal boot I get the KDE splash screen then a blank screen after log in, Thanks for the link I'll have a look now =)

---

### Post by compmodder26 on 2011-05-23
When logged in to Unity.  See if you can open a terminal by pressing "Ctrl+Alt+T".  If a terminal opens for you, then type "unity --replace" then hit enter.  Hopefully that will bring things back for you.

---

### Post by jamie1990 on 2011-05-23
Worked a treat the advice in the link you gave, just rebooted and got unity splash screen, many many thanks

---

### Post by compmodder26 on 2011-05-23
> **jamie1990 said:**
> Worked a treat the advice in the link you gave, just rebooted and got unity splash screen, many many thanks

Glad you got it sorted out!

---

### Post by collisionystm on 2011-05-23
> **jamie1990 said:**
> I recently installed KDE via the terminal using _**sudo apt-get install kde-standard**_ and I'm now having difficulty logging in and when I do finally log in all I get is a blank screen, I have tried booting ubuntu in safe mode and uninstalling KDE from the terminal but I am still prompted with the KDE log in screen after rebooting, I was just wondering how to get back to unity.

Any help would be great, many thanks in advance

```
sudo apt-get install tasksel
```

```
sudo tasksel
```

---

### Post by laihuining on 2011-08-17
> **compmodder26 said:**
> So, now that you've uninstalled KDE, do you get logged in to the Unity interface when you log in?

If that's the case then to get the Ubuntu log in screen, follow these instructions:

[http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/)

I have the same problem. now with your help of the link, I have work it out.
Thank you very much, with all my admire!

---

