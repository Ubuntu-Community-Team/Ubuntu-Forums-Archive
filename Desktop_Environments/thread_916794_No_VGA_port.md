---
title: "No VGA port?"
date: 2008-09-11
forum: Desktop Environments
---

### Post by robostang 548 on 2008-09-11
Hi,

I have a Compaq presario F572US laptop running ubuntu 8.04.  I was excited when I first put ubuntu 7.1 on my machine, I was excited about the external monitor/screen resolution gui.  I installed my Nvidia driver using the proprietary drivers manager and it worked great.  However, it wouldn’t recognize any attached external monitor or even that there was the capability for one.  I thought nothing of it cause I rarely ever use one.  Now, when I fresh installed 8.04, the proprietary driver didn't work.  I read somewhere that there was a problem with it and to install an old version of the driver from nvidia's website.  I did that but still I cant seem to get my external monitor running.  I read somewhere that there is a huge thing I have to add to my xorg.conf file to make it work but all the tutorials seem unclear about the approach.  Right now I'm thinking of going all ubuntu when I upgrade my laptops hard drive but the only thing keeping me holding on to windows is the fact that I need it to put up presentations on an external projector.  Any help would be greatly appreciated.

---

### Post by phidia on 2008-09-11
There is a wiki guide [here]("https://help.ubuntu.com/community/NvidiaMultiMonitors") for multi head or dual monitors.

---

### Post by robostang 548 on 2008-09-11
The tutorial didn't really seem to help.  When I go to the nvidia configuration panel, only one screen shows up for configuration.  There simply is nothing else.

---

### Post by robostang 548 on 2008-09-14
Solved the problem. I just installed the latest driver from Nivdia.  The only thing though is that I need the other monitor to be hooked into the port at startup or else Nvidia wont find it.

---

