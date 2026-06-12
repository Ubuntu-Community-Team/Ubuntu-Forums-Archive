---
title: "amaroK taking 100% of memory"
date: 2005-12-13
forum: Desktop Environments
---

### Post by Vulpus on 2005-12-13
Lately (past two weeks) I have been having problems with amaroK hanging up/crashing.  I have the system monitor running on my top panel and when amaroK is running it shows 100% memory usage "of which 60% is cache".  If i am just running amaroK it is not an issue but when I try to run anything else at the same time amaroK will hang up and the only solution is a re-boot.  NOT the sort of behaviour I expect from a Linux application.

Anyone else experienced this and possible have solution?  I have been using amaroK for 8-9 months and it is only lately that this has been an issue. (I am using 32 bit breezy on and AMD 64 with 512MB RAM)

---

### Post by cstudent on 2005-12-13
The Amarok website has a mention in their FAQ about 100% cpu usage. Don't know if it related to your problem or not.

With GStreamer-engine I'm getting 100% CPU usage while playing. How can I fix it? Here is what it says:



    When using GStreamer-engine with alsasink, amaroK requires the device to provide a mixer. Mixing allows multiple applications to access the device at the same time, and output sound simultaneously. This can either be achieved by using a soundcard with hardware-mixing (e.g. SBLive), or by using the "dmix" plugin for alsa, which provides software-mixing. See Setting up Dmix for ALSA. 

    After installation you need to specify "dmix" as the sound device in the engine settings dialog.

---

### Post by Vulpus on 2006-01-03
I have updated to the latest version of amaroK and that seems to have solved the problem.

---

