---
title: "desktop settings won't save in natty 11.04"
date: 2011-05-07
forum: Desktop Environments
---

### Post by kcredden on 2011-05-07
Ok, been poking around and found that at least Dolphin cannot save most of it's settings too. Another piece of the puzzle like below. 

Just installed Natty, and my monitor configurations won't save. I've seen this before in older Ubuntus, but now I cannot even find xorg.conf to edit it. 

I went too /etc/X11, but the only thing is a link from a file called 'x' to /usr/bin/Xorg but Xorg is a binary. 

So what do I do? I tried to set the Xorg file to chgrp/chown kcredden incase the permissions was causing the problem (which is what the older ubuntus did) but that didn't work. rebooting just switches it back to the default cloning. 

Help?

- Kc

---

### Post by RickSGM on 2011-05-09
I've got that happening to me too.  I just done a search on this very same thing and ended up here.

---

### Post by kcredden on 2011-05-09
Rick:

I just got done with the kubuntu forums as well. Even Kubuntu 11.04, 10.10 & 10.04 won't work. I even found where you can have Kubuntu install the nvidia drivers, and it hosed my system. So I hope you have better luck. I think after a week of trying about 6 debian distros, it'll be another 6 months to a year before this is 'out of the box' installing like 9.04 does. Myself, I'm buying a new non-nvidia card. My T22, (S3 video), and Asus Eee (an Intel video) had NO problems what so ever with Debian 6/KDE 4.6. 

Good luck!

- Kc


> **RickSGM said:**
> I've got that happening to me too.  I just done a search on this very same thing and ended up here.

---

### Post by RickSGM on 2011-05-10
Seems that nvidia also does bad on Ubuntu as well.  I tried it first, then tried Xubuntu.  Xubuntu done pretty fair.  Kubuntu, though, is wild.  I did toy around enough to get it to keep the background I want.  
I'm still using the basic driver, and not getting others until I know someone that has good luck.  I'll toy around a bit, but know just enough to be dangerous, so I have to be a bit careful.  lol

I know the nvidia drivers stink, though.  Whew!

---

