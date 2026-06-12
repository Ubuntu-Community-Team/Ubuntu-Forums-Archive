---
title: "How to make Bluetooth Audio headset work on ubuntu"
date: 2009-05-13
forum: General Help
---

### Post by j_benjamin on 2009-05-13
Dear All,

I have a PC which has the following version ubuntu and kernel:
Ubuntu 4.3.2
Linux version 2.6.28
gcc version 4.3.2 

I have installed the required bluetooth modules(l2cap, rfcomm, sco) and bluez packages using the apt-get install.  I followed the follwing wiki help documentation:
[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

The Bluetooth headset not getting detected:sad:. I am having a mono headset(HSP) device which I would like to connect to the PC.  

Whether anyone has faced this issue and resolved it? 

One more last question, whether I require the snd-bt-sco kernel module:confused:. I downloaded from the following link through CVS:
[http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)
but could not successfully compile since the code requires driver header file which for the linux 2.6.28 kernel is depreceated.

Please advice of the possible steps/configuration that I need to make to get the audio headset connect to the PC.

Thanks & Regards,
Benjamin

---

