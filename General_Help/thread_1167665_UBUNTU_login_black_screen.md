---
title: "UBUNTU login black screen"
date: 2009-05-23
forum: General Help
---

### Post by BlazeXI on 2009-05-23
Hello...

I need urgent help....

I installed ubuntu 9.04 about 2 weeks back and it's been working great no problems...the only thing is that I have a dell d630 and as we all know the compiz thing is not the best on this laptop model (best of integrated graphic card)...

today i wanted to disable the boot splash screen as i would like to see the grub instead... so i installed startup-manage and while at it installed the nvidia x server driver.... the only reason i installed the driver was because when i had ubuntu 8.10 this drive made compiz work great ...so i thought lets give it a shot...

anyway after successful installation i disable the boot splash screen via "startup-manage" when I restarted my laptop it ask me to choose a video driver ... so i did and then the grub shows no problems (normal boot to me) but then NO LOGIN SCREEN SHOWS JUST A BLACK SCREEN and i can't do anything no keys work nothing..... 

please help please ??????

---

### Post by Legace on 2009-05-23
Try this:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Screen%20Blanks/Monitor%20Turns%20Off](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Screen%20Blanks/Monitor%20Turns%20Off)

---

### Post by BlazeXI on 2009-05-29
Thank You


....I resolved this by going into recovery mode....then root console...and uninstalled all video drives...once done rebooted..

bobs my aunty ...hehehehe

Enjoy Your day :D

---

### Post by Hamburgian on 2009-06-06
I'm still new to all this Ubuntu stuff, but have noticed something about this 'black screen' at the grub screen **_AND_** if I turn the screen off while the PC is running for and leave it off for more than 15 mins..same thing...the default screen saver doesn't respond to keyboard or mouse clicks..just goes to black after 5 secs.

**However**, if I turn the screen off and then back on 5 or 6 times...clicking keys or mouse each time...eventually the screen comes back on.

So EITHER the screen doesn't know which driver to use..check synaptic package mgr...installed 9.04 yesterday and over 23 xserver-xorg-video drivers installed as default

OR the USB drivers for keyboard and mouse are asleep and take some time to reactivate.

P.S. Have tried just about all the 'fixes' given in these forums, including a clean install of 8.04, apart from removing ALL video drivers 
Nothing has worked. Didn't have the problem with 7.10.

Hope some one can help sort this out.

---

