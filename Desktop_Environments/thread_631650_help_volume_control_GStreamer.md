---
title: "help volume control GStreamer"
date: 2007-12-04
forum: Desktop Environments
---

### Post by cold37 on 2007-12-04
[SIZE="4"] i had ubuntu 7.04 and i up date it to 7.10 and i have no Volume control i can't hear anything it say No volume control GStreamer plugins and/or devices found. I lost the sound
What can I do ? i just got it from wal-mart here's the link to it [http://www.walmart.com/catalog/produ...ct_id=7779575#](http://www.walmart.com/catalog/produ...ct_id=7779575#) top[/SIZE]

---

### Post by tcommbee on 2007-12-04
do you have gstreamer0.10-alsa, gstreamer0.10-esd or libgstreamer-plugins-pulse0.10-0 installed, depending on your sound server? you can select the soundserver in system->preferences->"sound preferences" . any of them is okay if they work for you, esd or pulse maybe preferable (possibly the kind of server changed with the update). did you make any changes to your hardware i.e. sound card?

---

### Post by cold37 on 2007-12-04
ok i try that and i don't see anything but this--> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused <-- and no i did not do anything to make this happend

---

