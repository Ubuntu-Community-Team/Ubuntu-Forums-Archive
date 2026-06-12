---
title: "Ubuntu Crashing :o"
date: 2009-05-14
forum: General Help
---

### Post by Vrekk on 2009-05-14
Yes you read that right, Ubuntu 9.04 is acting unstable for me!!  It seems that if the computer is on for about 5 hours it locks up and i have to do a hard reset.  I don't know where the problem would be so i deiced to post here to see if you guys could help.

The one thing that i can think of is that my music player is causing it, because it is the only app that has been open and running for every crash, but there again i am almost always listing to music on this thing.  I did not have this problem until i did a clean install of 9.04 and made my separate/home.

So if there is anything you guys might be able to do, im game for just about anything.

---

### Post by khelben1979 on 2009-05-14
Have you tried to change to another music player?

Also if you are interested in what programs that may cause problems with instability, then you can always do this:
```
cd /etc/init.d/
```
from a text console

and then use the ```
man [name of the program]
``` command to check out what each application/script does and then decide if you still want the application in the system or not. 

Other than this, some Linux kernels can cause instability on some computer systems mainly due to how it is configured.

---

### Post by albinootje on 2009-05-14
> **Vrekk said:**
> Yes you read that right, Ubuntu 9.04 is acting unstable for me!!  It seems that if the computer is on for about 5 hours it locks up and i have to do a hard reset.

Is there anything interesting in the log files ?

Can you temporarily install the openssh-server and see whether you can still log in after a "freeze" ?

You can also try the magic system request key combination :
[http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html)
It is quite possible that you have to change the alt + "print screen" in the "Keyboard Shortcuts" settings before this will work.

And, perhaps not relevant, but I've installed Jaunty on two machines in the last few weeks where "noapic nolapic" was needed as extra boot parameters. Without those parameters one machine would have a weird behaving mouse and no network card would work (I tried three different ones), it was an irq problem. And the other machine would completely lose the network connection after a scp copy for longer than five minutes. 
With the extra parameters everything worked great.
See here for more information about extra boot parameters :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Vrekk on 2009-05-14
I dont think that the music app is the problem, i just saying its one of the few things that i always have running.  Is there a way i can (or you guys) view a system log that can lead to what the problem is?

---

