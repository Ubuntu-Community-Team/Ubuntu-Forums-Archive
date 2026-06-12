---
title: "Adobe Flash Player problem"
date: 2008-12-06
forum: General Help
---

### Post by 05rutterb on 2008-12-06
ok, today i installed Ubuntu 8.04 LTS Desktop Edition. It is my first time using it, and i am just managing to get to grips with it. However, when i went to watch my first video, it wouldn't work, and it said i needed to either turn JavaScript on (which i did) or install the latest version of Adobe flash player (which i did at [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/))
I downloaded the .deb for Ubuntu 8.04+, but it still came up with the same message when i tried to watch the video.
Help would be appreciated :D

---

### Post by RealPSL on 2008-12-06
Sounds like you installed Flash 10 from the Adobe site. First let us make sure that the installation was successful. You can check by typing "about:plugins" in the address bar of Firefox. You will see the following if it is successfully installed.

> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Note that unless you are really sure you want to run flash 10 you can install flash 9 from the repositories by going to Add remove programs on the menu and selecting to show all available applications then entering "adobe flash" in the search box. Note that you can only run one flash version at a time so if it is already installed and you want to change you must remove the previous version.

---

### Post by 05rutterb on 2008-12-06
wow, thanks, that helped a lot, flash player 9 works perfectly :)

---

