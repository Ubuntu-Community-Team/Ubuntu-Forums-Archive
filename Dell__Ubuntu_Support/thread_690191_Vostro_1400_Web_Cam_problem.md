---
title: "Vostro 1400 Web Cam problem"
date: 2008-02-07
forum: Dell  Ubuntu Support
---

### Post by ebsor on 2008-02-07
I have ubuntu installed on my my vostro 1400 and i cant activate the web cam. Please assist me on this.  Thank you.

---

### Post by linuxwizard on 2008-02-07
Try using Ekiga see if webcam is detected/works. Also you might have to change settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings there.

---

### Post by perlhead on 2008-03-13
The webcam works with the uvcvideo driver. which you can find at [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by rocksocke on 2008-03-28
thanx for the comment about the driver name "uvcvideo" and the link to the driverdownload.

i successfully installed the driver under a kernelcheck-compiled 2.6.24 running gutsy. yeah ;) just tested it with skype - works like charm for me!

---

