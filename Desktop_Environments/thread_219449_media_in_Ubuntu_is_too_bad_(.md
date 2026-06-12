---
title: "media in Ubuntu is too bad :("
date: 2006-07-20
forum: Desktop Environments
---

### Post by kdragon on 2006-07-20
i can't play any format popular media in Ubuntu :mp3,wmv .I open them with add on media player in Ubuntu :amarok,juk,Kaffeiene.I succed in adding to these media player but they don't play.And Totem Movie Player can't play  format,Help me pls.In 48 hours before i used Ubuntu,i can't hear any sound :(

---

### Post by palsyboy on 2006-07-20
Make sure /etc/apt/sources.list includes the following lines:
```
deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free
```
After that, run:
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree kmplayer libdvdcss2 libxine-extracodecs totem-xine-firefox-plugin vlc-plugin-alsa w32codecs wxvlc xine-ui xmms
```
That's probably more than you need, but it should work.

---

### Post by orb9220 on 2006-07-20
Open term and copy and paste into term

wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz)
tar -zxf easyubuntu-3.022.tar.gz
cd easyubuntu
sudo python easyubuntu.in

This will start up a gui and will allow you to install all the audio and video codecs that are needed.

The codecs to play music or video are not installed by default.

---

### Post by wieman01 on 2006-07-20
This link will help you set it all up in 3 steps (Realplayer, MP3, you name it):

[http://www.ehomeupgrade.com/entry/2663/how-to_get_full]("http://www.ehomeupgrade.com/entry/2663/how-to_get_full")

Should solve your problem once and forever. :-) Hope you like it.

---

### Post by kdragon on 2006-07-20
> **orb9220 said:**
> Open term and copy and paste into term

wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz)
tar -zxf easyubuntu-3.022.tar.gz
cd easyubuntu
sudo python easyubuntu.in

This will start up a gui and will allow you to install all the audio and video codecs that are needed.

The codecs to play music or video are not installed by default.

error:
> tar: easyubuntu-3.022.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kdragon@GRZ530:~$ cd easyubuntu
bash: cd: easyubuntu: No such file or directory
kdragon@GRZ530:~$ sudo python easyubuntu.in
python: can't open file 'easyubuntu.in': [Errno 2] No such file or directory

---

### Post by kdragon on 2006-07-20
> **wieman01 said:**
> This link will help you set it all up in 3 steps (Realplayer, MP3, you name it):

[http://www.ehomeupgrade.com/entry/2663/how-to_get_full]("http://www.ehomeupgrade.com/entry/2663/how-to_get_full")

Should solve your problem once and forever. :-) Hope you like it.

what's wrong with me??? 


[QUOTE=kdragon]kdragon@GRZ530:~$ sudo apt-get install totem-xine totem-xine-firefox-plugin libxine-extracodecs w32codecs libdvdcss2 flashplugin-nonfree sun-java5-plugin banshee streamtuner xmms skype msttcorefonts realplay f-spot
Reading package lists... Done
Building dependency tree... Done
Package totem-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libtotem-plparser1 libtotem-plparser-dev
E: Package totem-xine has no installation candidate[/QUOTE]

btw.thx for fast replying :D

---

### Post by kdragon on 2006-07-20
> **palsyboy said:**
> Make sure /etc/apt/sources.list includes the following lines:
```
deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free
```
After that, run:
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree kmplayer libdvdcss2 libxine-extracodecs totem-xine-firefox-plugin vlc-plugin-alsa w32codecs wxvlc xine-ui xmms
```
That's probably more than you need, but it should work.

error too
[QUOTE=kdragon]kdragon@GRZ530:~$ sudo apt-get install flashplugin-nonfree kmplayer libdvdcss2 libxine-extracodecs totem-xine-firefox-plugin vlc-plugin-alsa w32codecs wxvlc xine-ui xmms
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree[/QUOTE]

---

### Post by wieman01 on 2006-07-20
Are you using Dapper?

---

### Post by Dml on 2006-07-20
I'm lame and won't post shell commands there :P

Install automatix (you can install it with "synaptic"), then run it (system tools menu) and there you can select codecs etc and install them. There's few other nice things too. Worked for me.

---

### Post by Buffalo Soldier on 2006-07-20
Hi kdragon,

Glad to know after 48 hours of no music and you're still patiently with Ubuntu :)

OK, first things first. I would like to state that I prefer not to use any automated scripts or add any non-Ubuntu repositories. What I usually do to get my multimedia capability up and running is by following the [Restricted Formats](https://help.ubuntu.com/community/RestrictedFormats) guide at Ubuntu Guide User Documentation. 

Now, I hope you'll read the through the guide slowly, understand it and follow all the neccesary steps carefully. In the long run, understanding these things (such as why certain media codecs are not included) will help you to have a more fullfiling experience of the OS.

BUT, if you find yourself too lazy or you need the multimedia capabilities urgently... here is what short summary of what I usually do to get mine:[list]

[*] Enable universe and multiverse repository by typing **sudo gedit /etc/apt/sources.list** in the commandline and then editing the sources.list file. Here's an example of mine.

```
deb http://my.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://my.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://my.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe
deb-src http://my.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
```

[*] save that file and then run these commands to update all your current systems:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Restart your computer IF neccessary.

[*] then install these packages:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

[*] download Windows Codecs (w32codecs) by running this command:
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
```

and then install it by using this:
```
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```

[/list]

---

### Post by Ramses de Norre on 2006-07-20
Just as info: I think xine works far better than gstreamer (especially on things like wma), the needed packages are discribed at [http://wiki.ubuntu.com/RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats"). Try them out I'd say, I just wanted to mention the other possibility too.

---

### Post by Buffalo Soldier on 2006-07-20
> **Ramses de Norre said:**
> Try them out I'd say, I just wanted to mention the other possibility too.
Yeah, that is the best way to go.

---

