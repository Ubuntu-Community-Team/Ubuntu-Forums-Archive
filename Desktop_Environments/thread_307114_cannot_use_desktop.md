---
title: "cannot use desktop"
date: 2006-11-26
forum: Desktop Environments
---

### Post by zafar2002 on 2006-11-26
I have installed kubunto 6.10 first time at my friends house, where I used his monitor, but when I got home tried to reboot, it gives me error message of Ragne out of signal, it works fine with windows.

How can I manage to go to desktop from command promt? I tried ALt+F1 to Alt+F6 but no joy,it says X-server cannot connect

---

### Post by vtel57 on 2006-11-26
X does not recognize your monitor because you configured during installation using your friend's monitor. At the command prompt at boot up, type:

```
$ sudo dpkg-reconfigure xserver-xorg
```

This command will bring up the X configuration utility. Follow the directions. This should get you all fixed up.

Luck!

~Eric

---

### Post by zafar2002 on 2006-11-26
I will try this right now, thanks so much.](*,)

---

### Post by vtel57 on 2006-11-26
> **zafar2002 said:**
> I will try this right now, thanks so much.](*,)

I'll be online for a little while longer. Keep us posted on your progress. If I miss your answer, I'll be on again Sunday evening. It's 4:30AM here now... getting very sleeeeepy. ;)

---

### Post by zafar2002 on 2006-11-26
Vtel57, that was wonderful man, I was fighting with my computer since last three hours. I wish I knew this forum before. Where can I find these commands for future reference.

Thanks so much. It worked fine.:KS

---

### Post by vtel57 on 2006-11-26
That one is just one of many Debian tricks. Ubuntu is based on the Debian GNU/Linux distribution. Many long nights of reading, posting questions on forums such as this one, screwing your system up, and pulling your hair out will provide you with the knowledge and experience you seek, my son. Heh! :mrgreen: 

Glad you got it working, friend! Remember the most important thing... have FUN with it!

Regards,

~Eric

PS: Check out [THIS](http://forums.scotsnewsletter.com/index.php?showtopic=17087) very informative thread on a forum where I spend much of my time. It's an Ubuntu Links thread. Lots of great information there. Luck!

---

### Post by zafar2002 on 2006-11-26
Well you absolutely right, pulling my hair out, if I had any :-)

Now I am struggling with setting up my wireless, how do I detect my Netgear W614G router? I have a Lantech USB adapter, which access internet in Windows, but not sure how can I detect it in Linux? I will appreciate your help.

---

### Post by vtel57 on 2006-11-26
> **zafar2002 said:**
> Well you absolutely right, pulling my hair out, if I had any :-)

Now I am struggling with setting up my wireless, how do I detect my Netgear W614G router? I have a Lantech USB adapter, which access internet in Windows, but not sure how can I detect it in Linux? I will appreciate your help.

This is out of my realm of expertise, my friend. I would suggest that you post a new thread with this problem so others here can assist you.

Luck!

~Eric

---

