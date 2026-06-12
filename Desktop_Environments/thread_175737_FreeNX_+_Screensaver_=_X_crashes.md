---
title: "FreeNX + Screensaver = X crashes?"
date: 2006-05-13
forum: Desktop Environments
---

### Post by Exile29 on 2006-05-13
Over the past few days I have been experementing (unsucessfully, but that's for another thread) with FreeNX. 
Ever since I installed FreeNX, changed the ports, etc... I've noticed that whenever the screensaver comes on, I'll get a very colorful screen, then the login prompt comes up. I just figured that the screen is locking (like a security measure), but when I go into the screensaver settings interface it will do the same thing. I won't even get the chance to change any settings! What's worse, none of my previous session stuff is open. I'm afraid to walk away from my computer because I don't want to lose any work.
I removed FreeNX last night. That didn't help. 
Anybody have any ideas?

---

### Post by Exile29 on 2006-05-14
I also thougth I'd decsribe what it does when it crashes...
I get a screen that is black on top, and has multi-colored squares at the bottom. Then I get my nVidia logo screen, then I get the login window. This happens when I try to access the screensaver settings and when the screensaver starts (or trys to).

---

### Post by Exile29 on 2006-05-15
Another thing I would like to note: I have tried logging in with different accounts and I have the same issues. I guess that means that the problems I'm having aren't session specific. 
Also, just for kicks, I restored ssh_config and sshd_config to their original state (before the FreeNX install). Nada. ](*,) 

Ya... I'm keeping this bumped so everybody can see it.

---

### Post by clumpster on 2006-05-15
Hi...I have exactly the same provlem and im really frustrated...Ive been searching this for quite some time and havent found anyone with the same problem...Geez
I have found one solution:
I open gedit and i place a heavy object on keyboard just to keep pressing those buttons so screensaver wont activate....
For long periords of absence though you'll end up having either one heck of 1000-pages-long text file loaded in RAM or if you make a mistake and try this with a program other than the lighweight, you'll end up with a crashed system

---

### Post by clumpster on 2006-05-15
Found this

[http://www.ubuntuforums.org/showthread.php?t=174533&highlight=screensaver](http://www.ubuntuforums.org/showthread.php?t=174533&highlight=screensaver)

Apparently its not freeNX thats causing the problem but those damn kernel update....at least in my case its definately because of the online-update cause i remember when i last apt-get upgrade i started having this problem...So check the link of the thread above to see how to disable 3d screensavers and reinstall opengl drivers ...

---

### Post by clumpster on 2006-05-15
Found this

[http://www.ubuntuforums.org/showthread.php?t=174533&highlight=screensaver](http://www.ubuntuforums.org/showthread.php?t=174533&highlight=screensaver)

Apparently its not freeNX thats causing the problem but those damn kernel update....at least in my case its definately because of the online-update cause i remember when i last apt-get upgrade i started having this problem...So check the link of the thread above to see how to disable 3d screensavers and reinstall opengl drivers ...

---

### Post by Exile29 on 2006-05-15
Sweet!
Thanks clumpster. Hmmm... If I have FreeNX running, I could get this thing fixed right away. ;)

---

### Post by Exile29 on 2006-05-15
Thanks again for pointing me in the right direction! 
Sometimes the proper search terms elude me.
Anyhow, I reinstalled my nVidia driver (like everybody said, you'll have to reinstall 8756 every time after a kernel update) and it worked like a charm!


On a different note: I didn't know that the nVidia installer actually uninstalled the old driver (in this case, te same version compiled under a different kernel) before it installed. :???: 

In any case, I've got my old screensaver back! :mrgreen:

---

