---
title: "Got black screen after suspend/switch back from TV"
date: 2011-07-08
forum: Desktop Environments
---

### Post by blueocean123 on 2011-07-08
Hi,
I am newbie. I'm using Ubuntu 11.04 64bit. Mainboard Gigabyte GA-H55M-S2V. My LCD is a HDTV monitor which is plugged to onboard graphic card. 

I don't know what happen with my Ubuntu. It sometimes goes black when I try to wake my PC when it's suspended previously. The screen is black, but I still can move mouse cursor. I also can do blindly click on stuff on screen (I could play a song last time by clicking randomly).
This problem also happens sometimes when I switch back to PC from TV (My LCD is a HDTV monitor).

The only action I can do when it happened is reset my PC. It's terrible.

Please help.
Thanks a lot.

---

### Post by eino1953 on 2011-07-08
Try this Press CTRL+ALT+F1 This will take you tty. Then login using your user-name and password.
Then use the following to stop the gdm
> sudo  /etc/init.d/gdm stop
Then start it back up.
> sudo  /etc/init.d/gdm start

---

### Post by blueocean123 on 2011-07-08
> **eino1953 said:**
> Try this Press CTRL+ALT+F1 This will take you tty. Then login using your user-name and password.
Then use the following to stop the gdm

Then start it back up.

Thanks eino, I will try when it happens again. I'll let you know the result.


Well, it happened again today. I tried your solution. I worked but it was only 50% I was expecting.
- The screen was revoked successfully.
- But it looked alike I restarted my PC. No application remained :(

---

### Post by wildmanne39 on 2011-07-08
> **blueocean123 said:**
> Thanks eino, I will try when it happens again. I'll let you know the result.Hi, also have a look at this link, I personally disabled my screensaver and set power management to not turn anything off.

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by blueocean123 on 2011-07-13
> **wildmanne39 said:**
> Hi, also have a look at this link, I personally disabled my screensaver and set power management to not turn anything off.

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Thanks Wildmanne a lot. I think you pointed the problem correctly.

---

### Post by wildmanne39 on 2011-07-13
> **blueocean123 said:**
> Thanks Wildmanne a lot. I think you pointed the problem correctly.Hi, your welcome! if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

