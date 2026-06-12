---
title: "Webcam upside down on ASUS A52j"
date: 2019-03-10
forum: Desktop Environments
---

### Post by mama60 on 2019-03-10
Hi guys, Im a windows user generally, but for my mam's old laptop ASUS a52j xubuntu came as a great solution! 
So i've installed Xubuntu 18.04 x64 and found out that camera is flipped upside down in skype and other applications. 
I've installed guvcview and qt V4L2 test utility. Of course i have deployed libv4l and tryed to use it with skype shortcut as many times have seen in the internet.
Also I changed cam settings in Guvcview, nothing worked. 

As far as I suppose becouse that solutions was for older versions of linux in 2013-2016. Now skype and linux are updated. And those thicks doesn't work anymore... 

Plz help...

---

### Post by mama60 on 2019-03-10
the whole day was spent! I did it. Idk what was the difference but...
I've installed Insiders version of march 2019 from:

[COLOR=#000000][FONT=Arial][https://snapcraft.io/skype](https://snapcraft.io/skype) 


> sudo snap install skype --channel=insider/stable --classic
and then I modified the shortcut on my desktop this way:
> Exec=env LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so /snap/bin/skype %U[/FONT][/COLOR]
And then the camera works alright as I set it up in [B]guvciview
[/B]
May be this will be helpful for someone.

---

### Post by Tr1p on 2019-03-12
Or you turn your camera up side down

---

### Post by Jonathan Brian Francoeur on 2020-01-23
Did this solve the issue when using Cheese web cam or facebook messenger videos?

---

### Post by wildmanne39 on 2020-01-23
Hello Jonathan Brian Francoeur, the OP of this thread has not logged in since the day they posted this thread, if you need help please start your own thread, you are much more likely to get the help you need that way.

If you think it will be of help to you to get your issue resolved you can post a link to this thread in your thread.

Old thread back to sleep.

---

