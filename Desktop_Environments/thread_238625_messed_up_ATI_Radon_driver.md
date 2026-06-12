---
title: "messed up ATI Radon driver"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Ann667 on 2006-08-18
I was trying to install xgl/compiz and really seemed to have messed something up.  [This is the thread I used for instructions.]("http://www.ubuntuforums.org/showthread.php?t=216480&highlight=howto+ati+xgl")

I went through the first step and installed xorg-driver-fglrx, opened a terminal and did these comands: sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

I rebooted and the following happened.

1) my screen resolution changed from 1024x768 to 1600x1200.  I have a laptop and the screen is too small for this setting.  (I'm straining right now to even read what I'm typing, it's very small..)  If I try to set it back to 1024x768 the resolution of the screen is really bad.  

2) after I rebooted I typed "fglrxinfo" into the terminal to see if it worked and I got these error messages: (see attachment)

I'm not sure what happened.  I'd like to fix it so I can use xgl and compiz, but I'd also be happy with just getting my system back to how it was.  I didn't want to just try to uninstall xorg-driver-fglrx without asking advice.  

Thanks in advance for any advice.

Also, I wanted to add, I can't switch users.  If I try to switch to my admin user my system freezes up.

Some more information:  In the device manager, my card is listed as "Radeon R250 Lf [FireGL 9000]

---

### Post by Ann667 on 2006-08-18
I ended up reinstalling ubuntu…  (fortunately I’ve been saving my files on flash drives while I’m still learning this OS, just incase…)  Anyway, I was also unable to open up Open Office.  I needed to be able to use these programs so I figured it might just be a good idea to start all over this time.  

I’m going to attempt to install this driver again.  Can anyone tell me what I did wrong the first time?  I’m assuming it has to do with how I installed the driver.  I tried installing some other things last night, and even though those programs didn’t work, they didn’t seem to affect anything else.  It was after I tried installing the driver I had the problem.  Anyway, I’d like to avoid making the same mistake.

Thanks.

---

