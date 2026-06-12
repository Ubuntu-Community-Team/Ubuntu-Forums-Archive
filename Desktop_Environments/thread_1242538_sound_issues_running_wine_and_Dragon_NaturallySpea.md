---
title: "sound issues running wine and Dragon NaturallySpeaking"
date: 2009-08-17
forum: Desktop Environments
---

### Post by susancragin on 2009-08-17
There is only one way to get CSR (continuous speech recognition) on linux, and that is to run Dragon NaturallySpeaking through wine. 
Sadly, wine does not run with pulseaudio; and ubuntu seems to not run without it. 
Work-arounds are essential. But the directions to do them are changing constantly. 
As I type, with a 2.6.31-6-generic kernel, none of my work-arounds work, and I am without speech recognition. 

A couple of months ago, the fix was to apt-get purge pulseaudio, install esound, and use OSS. But now doing that makes some gnome components churn 50% of cpu looking for it. 
You could also use padsp oss. The sound using oss is not as good as alsa, but it was there. 

Pasuspender has not worked for a while. I don't know why this is.

Then a week or so ago I discovered that, if I booted up and entered 
killall pulseaudio in terminal, alsa worked, provided I had edited /etc/pulse/client.conf to un-comment out and change the following: autospawn = no

That worked GREAT until about Friday August 14 2009, when some update messed with it. 

Now ALL my methods produce timeout errors. 

Does anyone have any up-to-the second ideas that run on the current kernel, which is 2.6.31-6-generic?

---

