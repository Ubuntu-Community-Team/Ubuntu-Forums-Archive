---
title: "Webcam and audio problems on Dell XPS M1530 running Gutsy"
date: 2008-02-17
forum: Dell  Ubuntu Support
---

### Post by Aybara on 2008-02-17
Webcam:
When I try to open an application that uses the webcam, it say something like "Could not open video device (/dev(video0). Please check the connection. I have compiled and installed the latest version av the gspca module.

Audio:
The headphone jacks work fine, but the level on the right one is much higher than on the left one. I see no controls in alsamixer that fixes this. Worse, the mic is not working. I'm using alsa 1.0.14. Attached is an image showing the available channels in alsamixer.

This is on Ubuntu Gutsy.

---

### Post by linuxwizard on 2008-02-17
Are you sure you are using the correct driver ? Post results of the command >> lsusb. Have you tried using Ekiga ? You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by Aybara on 2008-02-18
Heyy. After playing around a bit it worked much better. V4L2 gave me a picture. Now I just gotta figure out what it takes to make Skype us it :-)

Edit: downloading the skype version that actually supports video helped :-)

---

### Post by linuxwizard on 2008-02-18
That's good to hear you got your webcam working.

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by Aybara on 2008-02-18
Yep. Thanks for posting.

---

