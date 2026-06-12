---
title: "Gnome 3 not using my graphics card"
date: 2011-06-03
forum: Desktop Environments
---

### Post by hotstepperk on 2011-06-03
Hello.

I have just upgraded my gnome version from gnome 2 and gnome 3 and its not working as I had hoped. The graphics seem laggy and when I go to aditional drivers, I see that my nvidia card, while active, is not in use. anyone have this problem? If so, how did you fix it. 

Thanks in advance.

---

### Post by maverick280857 on 2011-06-03
Install the proprietary driver *before* installing Gnome3, and see if Unity works. Then upgrade to Gnome3.

If you can't do another fresh install of Natty and Gnome3, then get the driver from [www.nvidia.com](www.nvidia.com), and install it manually. You might find [this]("http://leastaction.wordpress.com/2011/06/01/ubuntu-11-04-natty-narwhal-64-bit-guide-part-1/") and [this]("http://leastaction.wordpress.com/2011/06/01/ubuntu-11-04-natty-narwhal-64-bit-guide-part-2-installing-gnome3/") useful.

---

### Post by hotstepperk on 2011-06-03
> **maverick280857 said:**
> Install the proprietary driver *before* installing Gnome3, and see if Unity works. Then upgrade to Gnome3.

If you can't do another fresh install of Natty and Gnome3, then get the driver from [www.nvidia.com](www.nvidia.com), and install it manually. You might find [this]("http://leastaction.wordpress.com/2011/06/01/ubuntu-11-04-natty-narwhal-64-bit-guide-part-1/") and [this]("http://leastaction.wordpress.com/2011/06/01/ubuntu-11-04-natty-narwhal-64-bit-guide-part-2-installing-gnome3/") useful.

I had installed them beforehand. I was using unity since 11.04 was released and everything worked fine. Only this morning did I decide to make the jump.

---

### Post by hotstepperk on 2011-06-09
I've given up on it. re-installing ubuntu 11.04 now and wait for 11.10 with gnome 3. Thanks for the tutorial though. Any way to benchmark cuda improvements on the system?

---

### Post by maverick280857 on 2011-06-09
> **hotstepperk said:**
> I've given up on it. re-installing ubuntu 11.04 now and wait for 11.10 with gnome 3. Thanks for the tutorial though. Any way to benchmark cuda improvements on the system?

Why? Use the first link I gave you. The first post on that thread is how I've gotten Gnome3 to work on Natty. Just follow the instructions, things should work just fine.

I don't know what you mean by cuda improvements. Version 4 of the SDK doesn't work with gcc 4.5, so I am using version 3.2. It seems to be fast enough for me, but I'm not a power cuda programmer, so I wouldn't know..

---

### Post by hotstepperk on 2011-06-16
> **maverick280857 said:**
> Why? Use the first link I gave you. The first post on that thread is how I've gotten Gnome3 to work on Natty. Just follow the instructions, things should work just fine.

I don't know what you mean by cuda improvements. Version 4 of the SDK doesn't work with gcc 4.5, so I am using version 3.2. It seems to be fast enough for me, but I'm not a power cuda programmer, so I wouldn't know..

Sorry for the late reply. It kept breaking and telling my card (Nvidia 260GTX) couldn't be used or something.. can't remember the actual error message. I followed your instruction to the letter. Cuda's working great, so is java. Thanks

---

