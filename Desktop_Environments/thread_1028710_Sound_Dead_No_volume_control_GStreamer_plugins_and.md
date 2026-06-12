---
title: "Sound Dead: No volume control GStreamer plugins and/or devices found"
date: 2009-01-02
forum: Desktop Environments
---

### Post by sam-c on 2009-01-02
"No volume control GStreamer plugins and/or devices found"
I get this message when I try to open Volume Control. 
This Ubuntu 8.10 worked untill recently.

---

### Post by jeromestpierre on 2009-08-06
Hi know this is a very old post but since it came up as the first result on Google when I looked at how to resolve this issue I thought it would make sense to post here what worked for me. So here's the few commands I used to recompile the alsa drivers: 

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

I found it there: [http://www.fixya.com/support/t850063-ubuntu_sound_problem](http://www.fixya.com/support/t850063-ubuntu_sound_problem)

If you are wondering what the m-a command is as I did: [http://wiki.debian.org/ModuleAssistant](http://wiki.debian.org/ModuleAssistant)

I am running Jaunty 9.04 on kernel 2.6.28-13-generic.

---

### Post by crs0328 on 2009-08-06
Thanks for reviving this issue. I have the same issue and will try your suggestion tonight.

---

