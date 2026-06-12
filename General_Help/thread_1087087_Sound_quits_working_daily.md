---
title: "Sound quits working daily"
date: 2009-03-04
forum: General Help
---

### Post by sumpm1 on 2009-03-04
Hey guys. I have been using Ubuntu for about 6 months now, and this is my first recurring problem, not bad!

I leave my PC on 24/7. I usually have a Firefox browser left open. But when I get home, sound does not work in ANY programs. If I close Firefox and re-open it, then Firefox crashes. If I launch a music player or video player, they crash. If I log off and then log back in, the sound icon in the top right of the screen disappears. My solution thus far5 has been to reset the system.

What do I need to post so you guys can see what might be going wrong?

Thanks

---

### Post by renebs on 2009-03-04
You could start by looking at the output of this command:
$ ps ax > ~running_now.txt
This will list running applications to the file running_now.txt in your home. 
Particularly helpful is to run (after "closing" your firefox)
$ ps ax | grep firefox
to check if your firefox is still running, if it is, look for the PIDNUMBER and kill the application before you try to reopen it.
$ kill PIDNUMBER

---

