---
title: "Desktop freezes, keyboard mouse stops working, Nvidia 8800GT open sorce drivers"
date: 2014-10-07
forum: Desktop Environments
---

### Post by MechaMechanism on 2014-10-07
Ubuntu 12.04 worked greeat.  Upon upgrade to 14.04 I get seemingly random freezes.  The screen freezes and the keyboard stops working.  The mouse continues to work for a minute then freezes.  Only solution is to hard reset the power.  Does it again within a few minutes of logging in.  Version 14.04.1 64 bit with all updates.  Did fresh install, problem remains.  Using open source drivers.  Not using the Nvidia drives from Nvidia.

8800GT card.  All hardware in good condition and computer works great with 12.04, but not with 14.04.1.  Any help on how to solve this problem would be greatly appreciated.

---

### Post by Justgivemeaname on 2014-10-07
Hi,

Is this an Ubuntu-only install or do you have any other OS's installed? If so, does the other OS have issues too? 
Have you tried a Live CD/USB? Does the same happen? 
How did you check if your hardware is in good condition?

Does the Nvidia driver cause the same issues?

Do you normally have SSH access to the machine? Can you SSH in when it's frozen? If you are able to SSH in when it's frozen, please check: 
[LIST]
[*]processes that are running at that moment;
[*]the log for errors in /var/log (syslog and Xorg.0.log).
[/LIST]
If you find any that might seem related, please post them. I'm not sure if it will help us, but you might find something.

---

### Post by MechaMechanism on 2014-10-08
> **Justgivemeaname said:**
> Hi,

Is this an Ubuntu-only install or do you have any other OS's installed? If so, does the other OS have issues too? 
Have you tried a Live CD/USB? Does the same happen? 
How did you check if your hardware is in good condition?

Does the Nvidia driver cause the same issues?

Do you normally have SSH access to the machine? Can you SSH in when it's frozen? If you are able to SSH in when it's frozen, please check: 
[LIST]
[*]processes that are running at that moment;
[*]the log for errors in /var/log (syslog and Xorg.0.log).
[/LIST]
If you find any that might seem related, please post them. I'm not sure if it will help us, but you might find something.

Happens with live usb version 14.04.1.  Does not happen with 12.04.  Only ubuntu is installed. The Nvidia driver does the same thing.  I used live usb 12.04 to get the logs.  I see that the OS did a xorg crash dump in /var/crash.

---

### Post by MechaMechanism on 2014-10-08
See attached logs.

---

### Post by Justgivemeaname on 2014-10-08
I went through the logs you uploaded and I saw the errors. After a quick google I found a couple of bug reports that mentioned similar issues ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1285713](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1285713), [https://bugs.launchpad.net/nouveau/+bug/1309044](https://bugs.launchpad.net/nouveau/+bug/1309044), [https://bugs.launchpad.net/ubuntu/+source/webbrowser-app/+bug/1313077](https://bugs.launchpad.net/ubuntu/+source/webbrowser-app/+bug/1313077), etc.). Some of them where helped with trying the proprietary driver and some weren't (like you). If I understand correctly the driver is crashing.

Can you confirm if CLI still works, either through SSH or CTRL+ALT+F1, and use ```
top
```, for example? Is some process using a lot of resources?
If you are able to do so, can you check if there are any updates, install them and reboot?

---

### Post by MechaMechanism on 2014-10-10
> **Justgivemeaname said:**
> Can you confirm if CLI still works, either through SSH or CTRL+ALT+F1, and use ```
top
```, for example? Is some process using a lot of resources?
If you are able to do so, can you check if there are any updates, install them and reboot?

CLI does not work and neither does SSH.  My machine uses a static IP and when it crashes that IP is released so networking stops too which is why I believe the entire computer crashes.  CTRL+ALT+F1 does not work.

If I start the computer and don't log in using the GUI, but instead login using the CLI then everything is good.  I installed updates from the CLI and it still crashes.  I filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1378881](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1378881)  Tell me what you think.

---

### Post by Justgivemeaname on 2014-10-10
Yeah, after reading your post, it seems to be a bug that we can't resolve right here. At least, I wouldn't know how to at this point. I think you're right, filing a bug report is the best thing to do now. I subscribed to it, curious to see how this will end.

---

### Post by MechaMechanism on 2014-10-10
Thanks anyway.

---

### Post by bradgillap on 2014-10-11
I'm having this exact problem with ubuntugnome and it doesn't seem to matter if I use the open drivers or the closed drivers. It doesn't seem to be any different changing window focus modes. Sometimes I can find the active window and shake it around to get the rest of the desktop to start responding. I have had this issue with the gtx460 and the gtx770.

---

### Post by MechaMechanism on 2014-10-11
> **bradgillap said:**
> I'm having this exact problem with ubuntugnome and it doesn't seem to matter if I use the open drivers or the closed drivers. It doesn't seem to be any different changing window focus modes. Sometimes I can find the active window and shake it around to get the rest of the desktop to start responding. I have had this issue with the gtx460 and the gtx770.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1378881]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1378881")Click the button that says me too.

---

