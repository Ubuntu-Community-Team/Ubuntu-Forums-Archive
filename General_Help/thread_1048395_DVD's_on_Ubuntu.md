---
title: "DVD's on Ubuntu"
date: 2009-01-23
forum: General Help
---

### Post by dan_the_man on 2009-01-23
Hi guys, finally getting somewhere with linux, however Im having huge problems getting the 8.10 to play nice with commercial dvd's (with CSS).

I've installed VLC, Ogle and all the optional extras I can find for Movie Player and nothing seems to have helped. 

Any suggestions from the pro's?

---

### Post by diwas on 2009-01-23
I am sorry, but what is your problem? DVD won't read/mount/play?

---

### Post by khelben1979 on 2009-01-23
I did a quick search on this forum and found [this]("http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback") which might be of interest to you.

If this doesn't help. Post your hardware configuration and describe more in detail what problems you are experience'ing.

---

### Post by dan_the_man on 2009-01-27
> **khelben1979 said:**
> I did a quick search on this forum and found [this]("http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback") which might be of interest to you.

If this doesn't help. Post your hardware configuration and describe more in detail what problems you are experience'ing.

Had a flick though that post and did everything it suggested and it doesnt seem to have helped.. 

Diwas, Its mounting fine, the system recognises the disk but then refuses to play it. Movie Player provides this warning: "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"


I can confirm that libdvdcss2. 

As for the system Im running, its a Quad 6600 (3ghz), 8800gt, Asus P5Q-E... sorry guys, I have no idea about the CD/DVD drive..

---

### Post by philinux on 2009-01-27
Run vlc from a terminal, try playing the problem dvd. Post the output from the terminal.

---

### Post by stchman on 2009-01-27
> **dan_the_man said:**
> Hi guys, finally getting somewhere with linux, however Im having huge problems getting the 8.10 to play nice with commercial dvd's (with CSS).

I've installed VLC, Ogle and all the optional extras I can find for Movie Player and nothing seems to have helped. 

Any suggestions from the pro's?

You need to install the libdvdcss2 from Medibuntu.

Do the following in a terminal:
```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get update

sudo apt-get -y install libdvdcss2

```

You will be playing encrypted DVDs.

---

### Post by theozzlives on 2009-01-27
This has always worked for me:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
then:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by dan_the_man on 2009-01-30
> **stchman said:**
> You need to install the libdvdcss2 from Medibuntu.

Do the following in a terminal:
```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get update

sudo apt-get -y install libdvdcss2

```

You will be playing encrypted DVDs.

> **theozzlives said:**
> This has always worked for me:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
then:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Hi guys, did both these suggestions and rebooted.. and everythings working fine :D Great stuff, thanks for everyone's in-put, its greatly appreciated!

---

### Post by husky55 on 2009-02-02
Thanks guys. I also have the same DVD playing problem. This post will help greatly when I go to Ubuntu next time.

:p

---

