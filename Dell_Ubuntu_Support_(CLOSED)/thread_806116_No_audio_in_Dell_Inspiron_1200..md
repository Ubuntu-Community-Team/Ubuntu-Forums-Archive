---
title: "No audio in Dell Inspiron 1200."
date: 2008-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ubroshan on 2008-05-24
Hello everyone,

I have installed Ubuntu 8.04 server version in my laptop and it works fine.But I wanted to use it with ubuntu desktop package so I installed Gnome and KDE desktop packages one after another. And now Im facing a problem with my audio settings.That is I cannot hear any sounds or music on my laptop. 

But before I installed Ubuntu server version,I have been using desktop edition (Ubuntu 7.04 and then updated to 7.10 and 1 week before 8.04)for couple of weeks.But i did not experience any problem with sound settings.

Can anyone suggest me how to fix this problem? I will be grateful if anyone could help me on this.
My laptop manufacturer is Dell.Model:Inspiron 1200.

Thanks.

---

### Post by AWDriver on 2008-05-25
Take a look at [http://ubuntuforums.org/showthread.php?t=803956]("http://ubuntuforums.org/showthread.php?t=803956")

From my experience on an XPS 1330M:

Open the mixer, max all the playback levels (master, PCM, front, etc).  Tell it to show surround and the different channels in preferences (think that's where you pick it, don't have it in front of me, typing this from Vista).
Click select device, change between them and ensure the playback devices are all maxed.  This should be the case if you maximized them from the first step.

What you will need to do to control sound levels is use the PCM slider, not the master slider.  The master slider needs to remain 100%.  Right click the audio icon in the toolbar and select preferences.  Change the device to PCM and select the only option below it.  This will make the slider control the volume slider you need it to.

To have keyboard shortcuts control it instead of master, go to the "control panel"/select sound out of the system menu.  The last option in that sound control panel allows you to select what keyboard buttons will control.  Again, choose PCM.

---

### Post by ubroshan on 2008-05-25
Ahhh! Haaaa!

My audio is now working! Thank you AWDriver! My warm thanks to you!
It was my mixer had been muted automatically.I enabled it as you said and Walah! my sound is working.

Thanks again for your time.

Great job.Keep it up

---

