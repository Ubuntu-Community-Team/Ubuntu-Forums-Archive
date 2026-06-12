---
title: "Ubuntu 12.04 - Fresh Install Resolution Problem Nvidia 8600"
date: 2012-05-03
forum: Desktop Environments
---

### Post by killersoft on 2012-05-03
I just made fresh install and something with the drivers is wrong
I have a monitor with max resolution **1440x900**, but from setting monitor i can only choose max **1024x768**, no idea why.
Never before i've not have a problem like that.
I tried installing other drivers from "Additional Drivers" option but no result.

---

### Post by papibe on 2012-05-03
Hi killersoft.

Have you tried 'Monitors' to adjust the resolution?

Regards.

---

### Post by FormatSeize on 2012-05-03
> **killersoft said:**
> 
I have a monitor with max resolution **1440x900**, but from setting monitor i can only choose max **1024x768**, no idea why.


Same here. Xubuntu 12.04; nVidia GT545. 

I've had some difficulty with this card just recently when all of a sudden it stopped showing 14440x900, but that didn't surprise me at all since I've had this monitor for some time, and I've come to realize that 1440x900 is weird for some reason.

I have the nouveau drivers (or whatever comes out of the box with Xubuntu), but they don't want to give proper resolution. I have the proprietary drivers downloaded as well, but it's been a while for me, and I can't recall how I installed them before. I can't seem to find the right tutorial anymore, either, since that was quite some time ago. I think that it's "telinit something or other" and then some "sh" voodoo that only Linux users know, but I can't remember for the life of me how to get proper resolution out of this card in GNU/Linux.

---

### Post by killersoft on 2012-05-04
> **papibe said:**
> Hi killersoft.

Have you tried 'Monitors' to adjust the resolution?

Regards.

Yes i am a ubuntu user from 2-3 years never had a problem with the previos versions of ubuntu with my hardware

---

### Post by killersoft on 2012-05-04
> **FormatSeize said:**
> Same here. Xubuntu 12.04; nVidia GT545. 

I've had some difficulty with this card just recently when all of a sudden it stopped showing 14440x900, but that didn't surprise me at all since I've had this monitor for some time, and I've come to realize that 1440x900 is weird for some reason.

I have the nouveau drivers (or whatever comes out of the box with Xubuntu), but they don't want to give proper resolution. I have the proprietary drivers downloaded as well, but it's been a while for me, and I can't recall how I installed them before. I can't seem to find the right tutorial anymore, either, since that was quite some time ago. I think that it's "telinit something or other" and then some "sh" voodoo that only Linux users know, but I can't remember for the life of me how to get proper resolution out of this card in GNU/Linux.
I have experience with ATI and Nvidia over Linux
and i can say never had a problem with Nvidia
ATI is very hard to run proper resolution and 3d

---

### Post by kelvin spratt on 2012-05-04
> **FormatSeize said:**
> Same here. Xubuntu 12.04; nVidia GT545. 

I've had some difficulty with this card just recently when all of a sudden it stopped showing 14440x900, but that didn't surprise me at all since I've had this monitor for some time, and I've come to realize that 1440x900 is weird for some reason.

I have the nouveau drivers (or whatever comes out of the box with Xubuntu), but they don't want to give proper resolution. I have the proprietary drivers downloaded as well, but it's been a while for me, and I can't recall how I installed them before. I can't seem to find the right tutorial anymore, either, since that was quite some time ago. I think that it's "telinit something or other" and then some "sh" voodoo that only Linux users know, but I can't remember for the life of me how to get proper resolution out of this card in GNU/Linux.
1st uninstall Nouveau display driver
This is how I do it Since time began
put the driver in your home folder
hit ctrl alt f2   that takes you to a login screen
you should get username@username 
sudo sh NVI the press tab
 sudo sh NVIDIA-Linux-x86_64-295.49.run [this is my driver] then add this --no-x-check it will then look like this
sudo sh NVIDIA-Linux-x86_64-295.49.run --no-x-check  "press enter"
password
And the installer should start 
you will get some bla bla and click to continue
Then do you want to try and blacklist Nouveau display driver click yes
then it might tell you to reboot as the Ubuntu kernel does not automaticly release the driver.
Go through the process again and all should be well 
If you do it through jockey it does strange things and Nvidia is added to auto start after login hence it will not run correctly and double the ram used at idle.

---

### Post by reefis on 2012-05-24
i'm having the same resolution problem still with 10.04. i turn my computer on today and max display is all wrong. It must have been an new update i don't know

---

### Post by Martin Bannister on 2012-06-07
Has anyone managed to resolve this yet?  

I'm using the driver provided in Additional Drivers and can only get a Maximum of 1152x864 by using the Nvidia X Server Settings program (found by searching for nvid in the Dash).  

I get the option for 1440x900 in System Settings>Displays but when I select it I get this error...

> required virtual size does not fit available size: requested=(1440, 900), minimum=(320, 240), maximum=(1152, 864)I can't even determine what hardware it is at the moment other than it's NVidia.  

Thanks,
Mart.

---

