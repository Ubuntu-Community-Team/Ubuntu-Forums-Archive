---
title: "problems with video in firefox"
date: 2009-04-10
forum: General Help
---

### Post by Darthpc on 2009-04-10
I have Ubuntu 8.10 and the problem I have is some of the web video on some sites are not working. Am I using the right streamer? when I right click on video it tells me gnash is trying to run it. At first I thought it was just normal internet problems but the streams work when I switch back to my old windows installation. I am a new user of Linux and so far I love what I am learning so if you can point me in the right direction for resolving this issue I would greatly appreciate it   Thanks Darthpc

---

### Post by ivanvajar on 2009-04-10
Are you using 32bit machine?

---

### Post by ivanvajar on 2009-04-10
If you have 32bit computer try this in Terminal:

> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

---

### Post by ashwinhgtx on 2009-04-10
Use Synaptic Package Manager and search for Gnash. Remove it.
Then search for adobe flash player and install it.

---

### Post by ivanvajar on 2009-04-10
For 64bit:

> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar

---

### Post by Darthpc on 2009-04-10
yes it is a 32bit machine

---

### Post by ivanvajar on 2009-04-10
Run the code for 32bit machine from above. It will configure all codecs you need.

---

### Post by ivanvajar on 2009-04-10
...Including gnash removal and installing apropriate replacement that I'm using myself. :-)

---

### Post by Darthpc on 2009-04-10
Thanks everyone for the help i used the synaptic package manager and removed gnash flashplayer was already there so just the removal of gnash fixed the problem   darthpc

---

### Post by csh789 on 2009-05-21
> **ivanvajar said:**
> If you have 32bit computer try this in Terminal:

Thanks very much for this.  My gnash-dbg.log file was taking up my entire HD and causing videos to stutter and gmail to stop working in firefox.  Deleting the file worked but only temporarily as the log file continued to grow at great speed.  This script seems to have fixed the problem.  Thank you!

---

