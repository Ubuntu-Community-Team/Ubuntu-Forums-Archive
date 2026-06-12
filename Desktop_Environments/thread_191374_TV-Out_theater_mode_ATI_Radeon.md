---
title: "TV-Out theater mode ATI Radeon"
date: 2006-06-07
forum: Desktop Environments
---

### Post by gohan80 on 2006-06-07
Hi!

I've managed to get the tv-out feature to work with my ATI Radeon 9800 Pro card but when I play a movie with mplayer the movie window on the tv is all blank. I figure this is due to some overlay issue but I'm not sure how to configure it. If someone can help me with this I would be greatful. 

Another issue is that I would really like to have the option to play a full screen movie on the TV and do something else on my computer at the same time (i.e. the movie doesn't have to been full screen on my desktop). In Windows this is called Theater Mode but I cannot seem to find any settings for this in aticonfig. Is this possible in Ubuntu using ATI?

Thanks in advance.

---

### Post by toorima on 2006-06-07
Part C in this guide [http://www.ubuntuforums.org/showthread.php?t=96765](http://www.ubuntuforums.org/showthread.php?t=96765) can help you set up xorg.conf the right way for what you want, it's for nvidia but I did it in breezy for ati and it worked perfectly, haven't gotten around to do it in dapper yet so can't promise it will work but xorg haven't changed any that I know so should work.

---

### Post by gohan80 on 2006-06-08
I didn't get it to work following the guide, but I found a much easier way that basically does exactly what the guide is trying to make me do. All you have to do is to run "aticonfig --initial=dual-head --screen-layout=leftof" from the console. Even though this was not exactly what I was looking for when it comes to Theater Mode, it's close enough! Thank you very much for your help!

---

