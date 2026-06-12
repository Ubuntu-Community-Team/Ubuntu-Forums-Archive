---
title: "Can't get dvd's working with Kaffeine&amp;xine"
date: 2005-04-03
forum: Desktop Environments
---

### Post by J-Doe on 2005-04-03
I tried to search the forums on how to get dvds playing with xine but I haven't been able to get it to work...
I have dvdlibs installed and I have already enabled dma (I think?) :)
I read about some symlin to dev/dvd but how do I create one?

---

### Post by Lost on 2005-04-03
Well I am not exactly an expert but I think I work it out by finding a dvd decoder using synaptic. It works for me.

---

### Post by J-Doe on 2005-04-03
I think that Xine is the decoder engine...?
But I don't know if my dvd drive is wotking at all cause I can't find any dvd in my dev directory... allthough I remember seeing right names for my two dvd drives: asus and teac in some options settings...
so where is the problem?

---

### Post by mirtux on 2005-04-03
Hi,
 about the dvd is not necessary to have a /dev/dvd link, it works also if it points to /dev/cdrom (maybe you have to tell xine to search for dvd there). 
For dvd playing with xine (and others) you have to install the **libdvdcss2** libraries and **libdvdread3**.

Regards,
MC

---

### Post by J-Doe on 2005-04-03
[QUOTE=mirtux]Hi,
 about the dvd is not necessary to have a /dev/dvd link, it works also if it points to /dev/cdrom (maybe you have to tell xine to search for dvd there). 
For dvd playing with xine (and others) you have to install the **libdvdcss2** libraries and **libdvdread3**.

Regards,
MC[/QUOTE]

Okay, I have installed both of those and I set xine to search dvd from /dev/cdrom but I sitll get this error:
"The source can't be read.
Maybe you don't have enough rights for this or source doesn't contain data."

and following error:
"No plug-in to handle this resource (dvd:/)
xine: cannot find input plugin for MRL [dvd:/]
xine input plugin cannot open MRL [dvd:/]
xine: found input plugin : DVD Navigator"

Any ideas?

---

### Post by mirtux on 2005-04-03
Well,
   you  can try the two following things:
1) try to run xine as root
2) try also to install **libxine1** (but i think it is installed during xine set-up if you have used .deb files)

Regards,
MC

---

### Post by clb137 on 2005-04-03
HI,  

Have looked at the guide [http://ubuntuguide.org/](http://ubuntuguide.org/) for 'warty' and [http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/) for 'hoary' 

You need to download and configure as follows but the guide tells you all

1. add extra repositires

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

2. Install codecs

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs

3. DVD playback capability

sudo apt-get install libdvdcss2

4. Install xine-ui

sudo apt-get install xine-ui

5. Symbolic link

sudo ln -sf /dev/cdrom /dev/dvd
sudo cp /etc/udev/udev.rules /etc/udev/udev.rules_backup
sudo gedit /etc/udev/udev.rules

add the following line

# /dev/cdrom symlink
BUS="ide", KERNEL="hd[a-z]", SYMLINK="cdrom dvd"

(see the following sample file) [http://ubuntuguide.org/sample/udev.rules_symbolicdevdvd](http://ubuntuguide.org/sample/udev.rules_symbolicdevdvd)

good luck

clinton

---

### Post by clb137 on 2005-04-03
send me a message if you have problems

I will try to help you

clinton

---

### Post by clb137 on 2005-04-03
Please ensure that you DO NOT mix warty and Hoary in your sources list better to follow the following for you repositrie list

[http://ubuntuguide.org/temp/#extrarepositories](http://ubuntuguide.org/temp/#extrarepositories), then do the post i placed earlier sorry for any confusion


clinton

---

### Post by J-Doe on 2005-04-04
Okay, Thanks a lot ! DVD playback works now...kind of :) I now got the same weird problem that I had with windows. DVD's music and sound effects works fine but I ca't here the speech at all. I have a 5.1 surround system and I set xine engine to use 5.1 audio output.
I can't really remember what I did to get everything working in windows but I somehow reconfigured my ffdshow codecs.... what should I do know?

:)

---

### Post by clb137 on 2005-04-04
Hi

Does your sound work OK in the desktop? 

Try this in a terminal and let me now if your sound is ok 'Killall esd'

clinton

---

### Post by c_dog on 2005-04-04
What kind of sound card are you using? If you're not getting much volume for the speech on 5.1, it's probably because there's not enough levels on the center channel. I'll assume you've set the sound output for ALSA already also. OSS doesn't seem to support 5.1 yet. So, check the channel levels with alsamixer and pump them up on  both the analog and PCM center channel mixers.

---

### Post by J-Doe on 2005-04-04
I'm using Hercules Fortissimo 7.1 soundcard and using Alsa...
Sound works fine (although I still haven't found a way to decently configure subwoofer's volume levels) with everything else but dvd's have that weird problem :-s  :-k 
And I have tried to change those slider positions in kmix but haven't had any luck...

---

### Post by sparke67 on 2005-04-07
[QUOTE=clb137]HI,  

Have looked at the guide [http://ubuntuguide.org/](http://ubuntuguide.org/) for 'warty' and [http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/) for 'hoary' 

You need to download and configure as follows but the guide tells you all

1. add extra repositires

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

2. Install codecs

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs

3. DVD playback capability

sudo apt-get install libdvdcss2

4. Install xine-ui

sudo apt-get install xine-ui

5. Symbolic link

sudo ln -sf /dev/cdrom /dev/dvd
sudo cp /etc/udev/udev.rules /etc/udev/udev.rules_backup
sudo gedit /etc/udev/udev.rules

add the following line

# /dev/cdrom symlink
BUS="ide", KERNEL="hd[a-z]", SYMLINK="cdrom dvd"

(see the following sample file) [http://ubuntuguide.org/sample/udev.rules_symbolicdevdvd](http://ubuntuguide.org/sample/udev.rules_symbolicdevdvd)

good luck

clinton[/QUOTE]
 Thank you ! Thank you  !Thank you ! ... I am new to linux and this is the first thing I have been able to do at all. I have been trying to get DVD working for 2 weeks straight.

I will use your directions to go back and try and understand the actual commands ...

Thanks again .....

---

