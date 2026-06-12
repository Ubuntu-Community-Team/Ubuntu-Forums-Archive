---
title: "Vostro 1510 Ubuntu 9.04 Sound comes out of headphones and speakers concurrently."
date: 2009-09-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jmarques on 2009-09-25
Sound comes out of headphones and speakers concurrently on Ubuntu 9.04 on Vostro 1520.

How can I fix this?

Thanks

---

### Post by Denny Johnson on 2009-09-26
[http://ubuntuforums.org/showthread.php?t=604314&highlight=headphone](http://ubuntuforums.org/showthread.php?t=604314&highlight=headphone)
Post #6
Hope this helps.

---

### Post by Moses1200 on 2009-10-19
i have the same problem with vostro 1320, and this sulotion doesn't work for me. i have only 'master' and 'pcm' in my volume control. thx

---

### Post by nardo on 2009-11-17
I Solved the problem installing the last version of alsa drivers Version 1.0.21.
To see what version you have run 
```
cat /proc/asound/version 
``` 

I founded in this forum in Portuguese [http://ubuntuforum-pt.org/index.php?topic=56375.0](http://ubuntuforum-pt.org/index.php?topic=56375.0)
I translate:
Download the last versions of alsa-driver, alsa-lib and alsa-utils from [[COLOR="Navy"]AlsaProject[/COLOR]]("http://alsa-project.org/") 

Then remove alsa
```
sudo apt-get remove alsa
```
From where you downloaded alsa files

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

```
Compile and install the driver
```
cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install

```
Compile and install libs
```
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

```

Compile and install utils
```
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

```
Source:
[http://forum.ubuntuusers.de/topic/alsa-probleme-%2Bloesung/#post-1716322](http://forum.ubuntuusers.de/topic/alsa-probleme-%2Bloesung/#post-1716322)

> **Moses1200 said:**
> i have the same problem with vostro 1320, and this sulotion doesn't work for me. i have only 'master' and 'pcm' in my volume control. thx

---

