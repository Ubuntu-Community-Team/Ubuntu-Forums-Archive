---
title: "Creating a Custom Install .iso."
date: 2009-01-29
forum: General Help
---

### Post by Lee05162004 on 2009-01-29
Hi, so basically what I am looking for is a way to create an .iso that has certain programs and file on it that I want. That way I don't have to go around after a fresh install and reinstall all the software I like. I also have the Broadcom wireless chipset which requires the firmware be downloaded every time I do a reinstall. It would be nice simply to install one cd and have everything there already. Basically what I'm looking for is a program similar to nLite for Windows. I know there is APTonCD but it doesn't seem to give me the options I'm looking for. If I was to download the .deb packages is there a way I can slipstream them into an .iso? Thanks for the help.

---

### Post by avtolle on 2009-01-29
I've not tried this, but in reading other threads on the Forum, you might want to look into remaster.sys (do a search on it). From my limited understanding, this may well allow you to do as you indicate in your post.

---

### Post by mixmaster on 2009-01-29
remastersys is the way to go.

Tutorial here:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by Lee05162004 on 2009-01-29
Thank you, that's exactly what I'm looking for.

---

### Post by Lee05162004 on 2009-02-05
Over the past week I have done a clean install and installed all of the applications I wanted. I created a remastersys image and burned it to disc. I tested it out by running it as a live distro and it worked as far as I could tell although I didn't attempt to install it. One of the primary things I wanted to try was the wireless and when the live cd booted up the first thing I tried was to connect to a wireless network and it worked.

---

### Post by //yardo on 2009-02-05
Remastersys is sweet. I've used it to deploy web Kiosks that allow customers to log into my company website and purchase products.

The backup livecd .iso works perfectly

---

