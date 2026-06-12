---
title: "I Really Love it but..."
date: 2006-09-22
forum: Desktop Environments
---

### Post by seismicmike on 2006-09-22
I really love Linux and I really love Ubuntu but I gotta say I'm really pissed off right now. For two reasons:

1. No matter what I try there seems to be absolutely no way to configure my sound card and *nobody* seems to even have a clue how to fix it

2. Every fricking time there's a new release of ubuntu I have to completely redo ndiswrapper so that I can do wireless. And every time it's different. And every time it's more backward and counter-intuitive. And I still can't figure out how to do it in dapper. Shouldn't the updates have made it easier by now??? I mean Ubuntu developers know (don't they) that countless people have ndiswrapper problems. Wouldn't they have made it somewhat automatic by now? At least don't change something so I have to do it differently. I don't mind having to do it manually as long as I can do what I know to do without having to spend hours on the Internet hoping someone else has fixed it. I should at least be able to follow the same six steps I followed last time. Seriously folks, if Ubuntu is supposed to be Linux for Human Beings, they need to start fixing stuff like this. I mean, even Microsoft can figure it out, surely Ubuntu ought to be able to.

I really like Ubuntu and I want to stick with it but it's got major problems. If we can just figure out these two issues I might (just might) get rid of my dual boot and go completely Linux, but I'm lost without my internet and my music.

Anyway, sorry for the rant. I just had to vent. If anyone can fix my stuff, it'd be greatly appreciated.

---

### Post by gatiba on 2006-09-22
Give us more information on that problems, so we can try to help! ;)

---

### Post by CatKiller on 2006-09-22
> **seismicmike said:**
> I mean, even Microsoft can figure it out, surely Ubuntu ought to be able to.

I think you meant to say "I mean, even Microsoft can beat hardware manufaturers with a big stick until they make their drivers The Microsoft Way, surely Ubuntu ought to be able to reverse-engineer it so that it works for everyone all the time regardless of what equipment they're using and the differences between the driver and the underlying architecture."

---

### Post by seismicmike on 2006-09-22
> **CatKiller said:**
> I think you meant to say "I mean, even Microsoft can beat hardware manufaturers with a big stick until they make their drivers The Microsoft Way, surely Ubuntu ought to be able to reverse-engineer it so that it works for everyone all the time regardless of what equipment they're using and the differences between the driver and the underlying architecture."

Yes, you make a good point.

Ok here's what's going wrong. I've been over both issues elsewhere on the forum but I'll restate them. I have a laptop that is dual boot Windows/Dapper. In windows my sound workes perfectly fine, but the card has like 4-5 different drivers (i'm not kidding). In Linux however it does not work right. The only time I can ever hear anything is when I have my headphones plugged in and then it's only very very quiet (like I have to squint to hear it and it sounds like a whisper). Way back in the days of Warty Warthog, it worked fine. My laptop built in speakers didn't work, but if I plugged my headphones/external speakers in I had perfectly normal sound, but ever since breezy I've had this problem.

Here's all I can tell you about it:

```
username@ubuntu:~$ lspci
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```

That's it. I've opened every possible configuration editor for sound that everyone has ever suggested... all the equalizers and sliders in all the media players. I've done alsamixer and turned everything on and up and still I have nothing. The files play fine in Linux but I can't HEAR them.

Now... Wireless....

I (again) have a dual boot Windows/Linux laptop that came with built in wireless. When I first did my first installation of warty I had to get my built in wireless driver from windows and install it with ndiswrapper. It took me a while and I finally figured it out. Then I came over to Breezy and had to redo it (because at that point I had completely started over with a new installation of Windows and Linux). I finally got it to work and woo hoo.... Then something happened that made me have to reinstall windows all of a sudden. I don't remember exactly how but somehow GRUB got messed up and I had to completely wipe my hard drive. Thus I lost the copy of the driver on my hard drive. Then I went to download it from the gateway support website like I had done the last time except now they no longer have a copy of my driver... neither did Broadcom.... grrr... So, I bought a Belkin wireless card. I installed it in windows. copied the driver and ran ndiswrapper to good effect.

Woo hoo... it was working..... then along comes Dapper... and I didn't reinstall the os... I used aptitude to upgrade it... and all of a sudden ndiswrapper was screwed up. So I completely removed it and started over, following the exact same steps I did last time and it didn't work!

Here's what I did before.

```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```

to remove all previously installed versions of ndiswrapper

```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```

which all works fine except the -m part which gives me the error message:

```
modprobe config already contains alias directive
```

which I guess was ok... so anyway at this point my wireless card is supposed to work. In the past I would restart my laptop and the light on the card would come on in the install sequence. So good times. Except now it won't come on. I've tried

```
modprobe ndiswrapper
```

AND NOTHING HAPPENS... The light on my card never comes on. I'm supposed to have a card configured as a wlan0, but my network configuration wizard (System > Administration > Networking) lists lo, eth0, eth1 (i guess my old wireless card I don't have drivers for anymore that I don't use) and eth2 (apparently my new wireless card). WTF???????

```
username@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
```

```
username@ubuntu:~$ lspci
0000:02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
the bottom one is the one I want to use

```
username@ubuntu:~$ lspci -n
0000:02:09.0 0280: 14e4:4320 (rev 03)
0000:07:00.0 0280: 14e4:4318 (rev 02)
```

I tried doing a
```
sudo ndiswrapper -d 14e4:4318 bcmwl5
```

to make sure the driver was pointing to the correct card and it said,

```
Driver 'bcmwl5' is used for '14E4:4318'
```

But still nothing from my card.

I would like to point out that, for what it's worth, my card works perfectly in Windows.

---

### Post by l.tambiah on 2006-09-22
Compatible Hardware would be a good start ;-). I run Ubuntu on my tower Desktop and IBM Thinkpad Laptop. I chose the hardware carefully, and you know what I do not have ONE ISSUE, NOT ONE!!! And that goes for both machines. Ubuntu is not the problem, the hardware manufacturers are ;-).

---

### Post by seismicmike on 2006-09-22
I'll grant you that as well, but I bought my laptop before I even thought about linux and then when I got Ubuntu I didn't really have the money to go in for another computer, nor do I now.

---

### Post by l.tambiah on 2006-09-22
Some hardware just doesnt work well with Linux, in where you really have to go back to Windows I have seen this before. I always buy for GNU/Linux you see, so never have these issues. Sound can be a pain if you have unknown sound boards. Soundblaster is usually best for Linux, I have pure surround running through sound blaster. You should be able to get your wireless running though.

---

### Post by CatKiller on 2006-09-22
Caveat: I've neither used wireless networking nor ndiswrapper, and I don't know that much about how to make Linux do stuff.

Moving on. This bit:
> **seismicmike said:**
> 
which all works fine except the -m part which gives me the error message:

```
modprobe config already contains alias directive
```

Makes me think that this bit
> 
```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

```
to remove all previously installed versions of ndiswrapper
was not sufficient to remove the old configuration.

[This page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall") from the NdisWrapper project's Wiki suggests a different uninstall procedure, and appears to give some information on the files that you might need to remove.

Also, the page that had your old driver may have been cached by [the Wayback Machine]("http://www.archive.org/"). I found that useful when I was trying to find information on my old monitor, and you may find it helpful in the future.

---

### Post by CatKiller on 2006-09-22
Caveat: I've don't have the same sound chipset as you, I haven't had any problems with sound, and I don't know that much about how to make Linux do stuff.

Moving on.
> **seismicmike said:**
> 
```
username@ubuntu:~$ lspci
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```


[This page]("http://linuxmafia.com/faq/Debian/alsa.html"), which also talks about compiling sound modules from source, suggests that you should install these packages from the repository.
>     * alsa-base
    * alsa-headers
    * alsa-modules
    * alsa-oss
    * alsa-utils
    * alsamixergui

If you already have them, you could try a re-install of those packages to see if the scripts can re-detect your soundcard. The [ALSA Soundcard Matrix]("http://www.alsa-project.org/alsa-doc/") says that you should be using the snd-intel8x0 module. That module's page tells you some stuff about modules and how to configure them. Perhaps you can make some use of it.

---

### Post by haiku99 on 2006-09-22
the following howto worked for me using the same Broadcom drivers...the key part was to use the latest version of ndiswrapper...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by seismicmike on 2007-03-28
> **gatiba said:**
> Give us more information on that problems, so we can try to help! ;)

Dude, I give details every freaking time and nobody knows crap... If you really want to know, just search for stuff by me... I've posted several times in several different places.

I even posted somewhere a sweet script I wrote for hoary that made it all automatic for me, but since then, nothing.........

it's really freaking frustrating...

---

### Post by iamtherealwoody on 2007-03-28
Sorry if this issue is resolved or you have already tried this.  But I have ac97 ICH5 sound and I tried everything to get it working, no one could help either.  I eventually found it was one options in Volume Control, Center/LFE jack needed to be put to mixer output.  Sounds stupid but it took me over two weeks to eventually find that out. 

matt

---

