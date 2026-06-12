---
title: "1280x800 not possible on Sony VAIO"
date: 2006-08-07
forum: Desktop Environments
---

### Post by dihfg on 2006-08-07
When changing from XP to Dapper Drake I noticed that part of the screen on my VAIO PCG-791M is not used. Screen resolution is 1024x768 and cannot be changed to the optimum resolution 1280x800 @ 60Hz (15,4" WXGA). Changing xorg-conf manually or by running dpkg-reconfigure xserver-xorg showed no result.

Finally I found a hint on this forum from citronelu (june 5, 2006) suggesting to manually change xorg-conf by inserting a new modeline. This modeline you get by executing (in my case) gtf 1280 800 60 -x
Doing this I got
Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
Inserting this line in xorg-conf results in an error message, telling me that x-server could not be started, possibly wrong configuration and I had to go back to the original conf file.

Did I misunderstand citronelu's hint (I am quite new to Ubuntu) or is there another, VAYO specific way to force the display to 1200x800.
There is a method for ATI chips but Vayo uses Intel915GM Express Graphics Controller and I did not dare to try the ATI patch.

---

### Post by wieman01 on 2006-08-07
I have been using a Sony Vaio computer (VGN-270)and managed to configure it with a tool called "855resolution". Fairly easy to configure. Check this out:

[http://usefulinc.com/edd/notes/UbuntuOnSonyVaioTRSeries]("http://usefulinc.com/edd/notes/UbuntuOnSonyVaioTRSeries")

---

### Post by dihfg on 2006-08-07
Thankyou so much, Wieman01, for this great advice! I tried it and IT WORKS!

---

### Post by wieman01 on 2006-08-07
You're welcome. Another useful link, perhaps you need it one day:

[http://users.skynet.be/thomasvst/linux-on-laptop/]("http://users.skynet.be/thomasvst/linux-on-laptop/")

---

