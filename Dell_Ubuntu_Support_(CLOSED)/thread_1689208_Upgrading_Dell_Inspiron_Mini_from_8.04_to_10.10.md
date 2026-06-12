---
title: "Upgrading Dell Inspiron Mini from 8.04 to 10.10"
date: 2011-02-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dan Again on 2011-02-16
I've done a little reading on this subject and understand that there are some difficulties with updating a Dell Inspiron Mini running 8.04. I have two questions...

Is it a bad idea to attempt this upgrade? Will I "break" my computer?
If it's not a bad idea to attempt this upgrade are there any special steps that I need to follow or should I just follow the general instructions for installing off a USB stick? Are there any tweaks I should expect to have make afterwards? Are there any hardware components that simply won't work after making the upgrade (e.g. webcam)?

Thanks in advance for your help.

---

### Post by snowpine on 2011-02-16
If you are running the special Dell-branded Ubuntu that comes preinstalled on the Mini series, you need to back up all your data to an external drive and do a fresh reinstall of the new version. There is no upgrade path from "Dellbuntu;" it was a one-time, dead-end OEM release created especially for Dell.

Even if you are running "regular" Ubuntu 8.04 I would still recommend a fresh reinstall anyways, as 8.04 is three years old and a fresh install will allow you to take advantage of all the new features such as the ext4 filesystem.

Which model Dell Mini do you have? Depending on which model you have, you will need to do some tweaks to get everything working OK. You might find [this guide]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks") helpful, and of course you can use the forum Search feature to read existing threads specific to your model of Dell Mini.

---

### Post by Dan Again on 2011-02-16
Thank you so much for your response! What you've said pretty much matches my expectations based on the small amount of research that I've done, but I just wanted to hear from somebody a little more experienced than myself that I wasn't going to "break" my computer. I will attempt this upgrade soon and report back on how it goes.

---

### Post by snowpine on 2011-02-16
Which model of Dell Mini do you have?

---

### Post by Dan Again on 2011-02-16
Not exactly sure, as I inherited it from my father. Bottom of the computer says Inspiron mini 10; model PP19S.

---

### Post by snowpine on 2011-02-16
I believe that model PP19S has the infamous GMA500 "Poulsbo" graphics (type 'lspci | grep VGA' into a terminal if you're not sure), so you will definitely need to do some tweaking.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

---

### Post by Dan Again on 2011-02-16
Hmmm...that's what I was kind of worried about. Been doing a little bit more research and it looks like there is a tweak to get the resolution right, but this leaves the video playback broken. Don't think I'm willing to give up video playback. Am I reading these threads correctly?

---

### Post by snowpine on 2011-02-16
I am not personally familiar with the GMA500 hardware, so all I can do is point you in the right direction for answers.

If you can't find the information you need at Ubuntu Forums, you can take a look at [http://mydellmini.com](http://mydellmini.com) for some great how-to's. 

Another user had success with PCLinuxOS on his Dell Mini 12 [in this thread]("http://ubuntuforums.org/showthread.php?t=1686744").

---

### Post by Dan Again on 2011-02-16
Installing now...

---

### Post by PRC09 on 2011-02-16
Another Dell Mini link.....


[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by Dan Again on 2011-02-16
All done...things seem to be working well. Just watched a YouTube video in full screen and it looked pretty good. One little hiccup - I added the last two lines of code to the xorg.conf file (the ones the author said to add at your own risk), and they borked things up. Computer booted to terminal. Had to go back in and edit the xorg.conf file through nano, but once I removed the troublesome two lines was able to get right back in to Gnome. Woot! Thanks for all your help!

---

### Post by Dan Again on 2011-02-16
Hmmmm...okay, just noticed that YouTube videos play very choppy in HD. Relatively minor, but would be nice to get it fixed. Any ideas?

---

### Post by Dan Again on 2011-02-16
Also webcam video recording is terrible.

---

