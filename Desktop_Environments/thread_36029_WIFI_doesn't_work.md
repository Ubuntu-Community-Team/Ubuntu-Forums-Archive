---
title: "WIFI doesn't work"
date: 2005-05-21
forum: Desktop Environments
---

### Post by -starter- on 2005-05-21
Hi,

I'm not quite sure if this is the right place for this thread.

Anyway, I have Problems with Ubuntu on my Laptop Asus Z7700R with an Intel ProSet-WiFi-Card 2200B

The wireless LAn-Connection is set properly and works sometimes (espacially when i used my secondary OS winXP before) but even then cuts the connection after some minutes.

So the Problem is that i doesn't work in over 90% of all cases.
All settings seem to be normal. (Note: when i was using SuSE 9.2, I had to install a special firmware-rpm).

Does anybody know how to fix this? I can't use an OS without Internet access.
Thank you!!

---

### Post by philipacamaniac on 2005-05-21
Mods, can you move this over to Hardware -> Networking?

-starter-, here is a howto on getting your Intel 2200B (ipw2200) working: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by -starter- on 2005-05-30
thanks for the answer. ubuntuguides is what i've been searching for long.

However, they don't tell me how make the 'make'-command work. I need the make-command in order to install my WIFI-card.

(I installed the Add-on-cd but with no effect.)

Thanks!

---

### Post by philipacamaniac on 2005-05-31
You need the following packages: build-essential, linux-headers-2.6.10-5

```
sudo apt-get install build-essential linux-headers-2.6.10-5
```

---

### Post by -starter- on 2005-05-31
it still doesn't work. Every time i type 'make' an error occurs:

/lib/ ... /build directory doesn't exist.

So the sources are missing? What to do now :-| 

(Note: I am not able to connect to the Internet jet because of the missing wlan-drivers. I can only download files via my Windows-PC and burn them. i.e. I can't use synaptics-manager )

---

### Post by usererror on 2005-06-01
do you have a built in LAN card that you could download drivers with?

can you copy and paste the exact errors you are getting when you try the make command somehow?

---

### Post by darkrad on 2005-06-01
[QUOTE=-starter-]it still doesn't work. Every time i type 'make' an error occurs:
/lib/ ... /build directory doesn't exist.

So the sources are missing? What to do now :-| 
[/QUOTE]

Make sure there is a link to the kernel source from the modules directory. /lib/modules/VERSION/build should be a link to the kernel source, where VERSION is the version of the kernel you are running. If there is no link, you'll get an error at the make install step. To create a link, assuming the kernel sources are present, use the command:

```
ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build
``` 

(source: [http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation))

Hope it helps.
Bye.

---

