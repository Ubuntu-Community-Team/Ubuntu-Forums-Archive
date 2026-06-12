---
title: "Cannot watch any movies"
date: 2005-10-13
forum: Desktop Environments
---

### Post by escuchamezz on 2005-10-13
Seriously I cannot view ANY movies that I have with totem, what application should I install Xine or mplayer? how do i do it?

Also when I try to add realplayer in "add applications" i get this:

The file /root/rp8_linux20_libc6_i386_cs2_rpm does not exist, or it is corrupt. You may have downloaded the wrong file, or put it in the wrong location. Please try again.

If the file you downloaded has a different name, the filename may have changed since this installer was last updated. You can still try to use the installer; just rename the file you downloaded to /root/rp8_linux20_libc6_i386_cs2_rpm . Note that if you do this, there is no guarantee the installer will work.

---

### Post by invalid on 2005-10-13
As for the first problem:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
See How to install Multimedia Codecs?
and below that, How to install Multimedia Player (xine-ui)?

Someone else may be able to answer the second half.

Cheers,
Cb

---

### Post by xeta on 2005-10-13
Easy Ubuntu might be the easiest way.

[http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23)


Only check "Multimedia", and make sure you **UN**check the rest of the items as they haven't been fully successfull on 5.10.

---

### Post by luckyaba on 2005-10-13
i like gmplayer but there isn't a 64 bit version to my knowledge so i am using xine.

Are you sure you got the right installer? install instructions are there too

[http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner](http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner)

---

### Post by escuchamezz on 2005-10-13
[QUOTE=invalid]As for the first problem:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
See How to install Multimedia Codecs?
and below that, How to install Multimedia Player (xine-ui)?

Someone else may be able to answer the second half.

Cheers,
Cb[/QUOTE]

gstreamer0.8-plugins - unmet dependancies
w32codecs - not found
libdivx4linux - not found
sox - unmet dependancies
ffmpeg - unmet dependancies
vorbis-tools - unmet dependancies

---

### Post by escuchamezz on 2005-10-13
[QUOTE=luckyaba]i like gmplayer but there isn't a 64 bit version to my knowledge so i am using xine.

Are you sure you got the right installer? install instructions are there too

[http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner](http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner)[/QUOTE]

i get this:

/Desktop$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by luckyaba on 2005-10-13
I think you need to install gcc.

try apt-get install gcc

---

### Post by invalid on 2005-10-13
sudo apt-get install build-essential

Cheers,
Cb

---

### Post by imad_b on 2005-10-13
Hi,
I also can't watch any movies.
I followed the instructions from: 
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) which say this:
```
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8
```

When I tried to run this in Terminal, it came up with this:
```
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-cdio gstreamer0.8-festival gstreamer0.8-gtk gstreamer0.8-jack
  gstreamer0.8-mad gstreamer0.8-mikmod gstreamer0.8-mms gstreamer0.8-mpeg2dec
  gstreamer0.8-sid gstreamer0.8-swfdec jackd liba52-0.7.4 libcdio3 libid3tag0
  libjack0.80.0-0 libmad0 libmikmod2 libmms0 libmpeg2-4 libsidplay1
  libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-cdio gstreamer0.8-festival gstreamer0.8-gtk gstreamer0.8-jack
  gstreamer0.8-mad gstreamer0.8-mikmod gstreamer0.8-mms gstreamer0.8-mpeg2dec
  gstreamer0.8-plugins gstreamer0.8-sid gstreamer0.8-swfdec jackd liba52-0.7.4
  libcdio3 libid3tag0 libjack0.80.0-0 libmad0 libmikmod2 libmms0 libmpeg2-4
  libsidplay1 libswfdec0.3
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded.
Need to get 1290kB of archives.
After unpacking 3781kB of additional disk space will be used.
Do you want to continue [Y/n]?
Abort.

```

Why does it abort?  I chose Y of course.

---

### Post by invalid on 2005-10-13
That is very interesting..
Something though that you would probably get answered better if you started a new thread

Cheers,
Cb

---

### Post by Gandalf on 2005-10-13
Do the following...
```

wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
sudo apt-get install totem-xine

```

and now everything should work

---

### Post by ktulu1115 on 2005-10-13
[QUOTE=escuchamezz]gstreamer0.8-plugins - unmet dependancies
w32codecs - not found
libdivx4linux - not found
sox - unmet dependancies
ffmpeg - unmet dependancies
vorbis-tools - unmet dependancies[/QUOTE]

Not finding libdivx4linux shouldn't be a problem, I couldn't find it either in the repos - but AVIs still seem to play fine on my box.  I installed the following packages (and dependencies obviously) and all is OK for the moment:

ffmpeg
gstreamer0.8-ffmpeg
gstreamer0.8-plugins
totem-xine

I'm assuming DivX is part of w32codecs, so just follow instructions above and all should be good.

---

### Post by imad_b on 2005-10-15
[QUOTE=Gandalf]Do the following...
```

wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
sudo apt-get install totem-xine

```

and now everything should work[/QUOTE]

Thanks Gandalf.
I did that, and it seemed to install everything ok.
But I still got errors when playing a WMV file (haven't tried others yet)
Please see the attached error message.

---

