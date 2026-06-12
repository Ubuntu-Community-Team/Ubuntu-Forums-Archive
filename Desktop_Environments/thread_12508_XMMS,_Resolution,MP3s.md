---
title: "XMMS, Resolution,MP3s"
date: 2005-01-25
forum: Desktop Environments
---

### Post by ramtajogi on 2005-01-25
Hi!
I am a new user of Linux though I am trying hard to get Linux installed on my system for long. But it seems that most Linux distributions are not compatible with my video card i.e- SiS 630E.
I tried to install Redhat,Knoppix,SuSe 9.1 Personnal,Gentoo before but all I managed to get a blank screen staring and poking fun at me. It was a pleasent surprise to me when Ubuntu readily recognized my display card and I got a GUI installation screen. What a relief and not only it recognized graphics card but most of the associated hardware including HP-3420 deskjet printer. But like most good things in life this was also shortlived. As now I got a myraid of problems. First of all, I am unable to install any new software say XMMS. As per the readme file when I typed ./configure at the $ prompt it threw these lines on me 

root@ubuntu:/home/sandeep # cd xmms
root@ubuntu:/home/sandeep/xmms 
# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH See `config.log' for more details.
root@ubuntu:/home/sandeep/xmms #


Although I can hear *.ogg files but unable to play *.mp3 files. What I need to download in order to play mp3s and how to install that.

Also, I am unable to change my screen resolution from 1024*768 to 800*600. Though System Configuration> Screen Resolution shows in the drop down list  800*600 resolution but when I try to change it blank screen comes and after some time previous resolution is restored. Strangely enough I easily switch to 640*480 resolution. I even tried to go for lesser refresh rate in 800*600 mode but to no avail. I am using the same resolution 800*600 with a refresh rate of 85 on my Windows Me and XP.

Please help.

---

### Post by Rule on 2005-01-25
hey to compile things install "build-essential" from synaptic you can get xmms from there also so no need to compile anything  :D

---

### Post by Perfect Storm on 2005-01-25
No need for compile xmms, grab it at 'synaptic Package Management' ( 'computer' tab ---> 'system configuration' ----> 'synaptic Package Management')

But before that read this before advancing futher: [http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)

---

### Post by ramtajogi on 2005-01-25
No XMMS package is there in the synaptic Package Management. Also, I guess there is no inherent MP3 support in Linux due to some legal issues. So, is there any plugin needed to listen mp3 files. Also, I want to know how to install other applications like media players etc without Synaptic package management just like in any other linux distro by  using commands like ./configure,make,makeinstall.
**Please tackle my screen resolution problem too **as 1024*768@60 Hz is not too pleasent on my eyes (87 Hz refresh rate is not supported). Plz suggets something to make it 800*600@85 or so.  System Configuration> Screen Resolution is not working for no apparent reasons for 800*600. 
If 1024*768 is supported then obviously lesser resolutions must also be supported.

---

### Post by Moobert on 2005-01-25
xmms is there :)

you need to first add extra locations to the apt system:

[http://ubuntuguide.org/index.html#extrarepositories](http://ubuntuguide.org/index.html#extrarepositories)

maybe get more codec (not sure if mp3 needs this, but it will add quicktime ect)

[http://ubuntuguide.org/index.html#codecs](http://ubuntuguide.org/index.html#codecs)

then get one of the many sound players on linux:

xmms, totem, mpg321, and rhythm box.

off synaptic or by using;

sudo apt-get install xmms

also installing totem-xine, helps stuff like nautilus play files.

as for the screen res problems, ifthe gui isn't working your need to edit your xfree config... and add more valves it lives in:

/etc/X11/XF86Config-4

edit in a normal text editor like gedit, (i'd read some xfree86 guides first)
BUT backup first.. AND know how to replace the config with out X :)

---

### Post by burlap on 2005-01-25
> I am a new user of Linux though I am trying hard to get Linux installed on my system for long. But it seems that most Linux distributions are not compatible with my video card i.e- SiS 630E.

Check this out: [http://www.winischhofer.net/index.shtml](http://www.winischhofer.net/index.shtml)

---

### Post by ramtajogi on 2005-01-27
Phew!!! Ain't anybody here know how to install XMMS without using Synaptic Package Manager. I don't have net connection for my Linux machine so Synaptic manager says downloading failed after I perform the steps as given in :

[http://ubuntuguide.org/index.html#extrarepositories](http://ubuntuguide.org/index.html#extrarepositories)

Though I have a CD of XMMS and other Linux utils but don't know to install them.

---

### Post by Perfect Storm on 2005-01-27
If you have Xmms on CD then copy the .deb file on your computer.

cd /where/you/saved/the/file
sudo dpkg -i <name>.deb

or

sudo dpkg -i /where/your/deb/file/is/<name>.deb

---

### Post by ramtajogi on 2005-01-28
Thanks Artificial Intelligence. I'll try that and let u know about that.  8-)

---

### Post by Jad on 2005-01-28
[QUOTE=ramtajogi]Thanks Artificial Intelligence. I'll try that and let u know about that.  8-)[/QUOTE]
 Salam 
Check this
Ubuntu Multimedia How to 
[http://ubuntuforums.org/showthread.php?t=94](http://ubuntuforums.org/showthread.php?t=94)

---

