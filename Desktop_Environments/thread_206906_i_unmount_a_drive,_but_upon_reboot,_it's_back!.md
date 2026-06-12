---
title: "i unmount a drive, but upon reboot, it's back!"
date: 2006-06-30
forum: Desktop Environments
---

### Post by syxbit on 2006-06-30
it took me a while to figure out how to unmount.
common sense told me it was unmout, but it's ```
sudo umount sda1
```
as soon as i reboot, the drive becomes mounted again. (it's actually my windows partition)
any ideas ?
thanks

---

### Post by falcon15500 on 2006-06-30
Yeah, the drive is listed in your /etc/fstab file - which means it will be mounted at boot.  Why don't you want it mounted?  Don't you want to be able to access your windows partition from linux?

falc

---

### Post by taurus on 2006-06-30
It's 
```

sudo umount /dev/sda1

```
And if you don't want to mount it, then either remove the entry in your /etc/fstab for it or place a # in front of it...
```

sudo gedit /etc/fstab

```

---

### Post by syxbit on 2006-06-30
thanks guys
i was doing
```
sudo umount /media/sda1
```
as for why i don't want access to windows?
i don't use it. just to play DVD's (totem sucks)

---

### Post by syxbit on 2006-07-01
come on, help guys!
this is a serious issue (and the only reason i still dual boot with windows)

---

### Post by catlett on 2006-07-01
I don't understand your problem. Do you not know how to edit your /etc/fstab? Here's a good how to. [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) But basically all you have to do is run ```
sudo apt-get gedit /etc/fstab
``` nWhen it opens just delete the line with /dev/sda1.
And totem doesn't suck if you install totem xine and all the plugins etc. Have you ever installed XP and tried to play something in Windows Media Player? All it will do is play a radio station. Yopu have to buy all the codecs for mpeg,dvd etc. If you bought a pc with XP installed part of the price went to loading Intervideo or Power DVD.

Install totem-xine first 
```
sudo apt-get install totem-xine
``` Then install the plugins etc 
```
sudo apt-get install libxine-extracodecs
sudo apt-get install gstreamer0.10-ffmpeg
sudo apt-get install gstreamer0.10-gl 
sudo apt-get install gstreamer0.10-plugins-base 
sudo apt-get install gstreamer0.10-plugins-good 
sudo apt-get install gstreamer0.10-plugins-bad 
sudo apt-get install gstreamer0.10-plugins-bad-multiverse 
sudo apt-get install gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
sudo apt-get install libdvdcss2
```

---

