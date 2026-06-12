---
title: "Audio output is not working"
date: 2005-07-07
forum: Desktop Environments
---

### Post by Djeepy46234 on 2005-07-07
Hi

When I try to play some music on ubuntu, it's not working. Sound is not working at all ...

I have a **Intel 82801FB ICH6 - Azalia Audio Controller**  audio card...

Someone help me please

Have a nice day :)

---

### Post by zoofields on 2005-07-08
You tried to play music and it's not working--is this a new install?  What sort of music are you trying to play--mp3, ogg, music from a CD?  Are there any error messages?  And, I can't be sure from the way you worded it, but will just music not play or do you have no sound at all?  Also, what program are you using to try to play music?

We'll be better able to help if we know these things.

---

### Post by JOKe on 2005-07-08
my problem is that XMMS and beep-media-player with outpout : OSS dont work .. they CRASH ? why is this ? 
p.s. if there are at eSOUNd it works gnome sounds works too and totem works.

---

### Post by bigblop on 2005-07-08
I have the same problem with an onbard soundcard, it worked fine before in warty.

johs@ubuntu:~$ cat /proc/asound/cards
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with CMI9761 at 0xdc00, irq 18
johs@ubuntu:~$


johs@ubuntu:~$ sudo lspci -v | grep -i audio
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
johs@ubuntu:~$


johs@ubuntu:~$ dpkg -l|grep alsa
ii  alsa-base      1.0.8-4ubuntu4 ALSA driver configuration files
ii  alsa-utils     1.0.8-1ubuntu1 ALSA utilities
johs@ubuntu:~$

---

### Post by Djeepy46234 on 2005-07-08
It's a fresh install of Linux, all kind of sound aren't working except motherboard beep (in console)...

CD MP3, OGG, all not working, video too. With Totem, I have this error message :

```
Resource is not available
``` 

I tried all the programs :

MPlayer
Totem
Kaffeine

That's really like this... And also Gaim have no sound.

---

### Post by jcohen on 2005-07-08
Response to Joke:

OSS is the default plugin for XMMS. I'm not sure why it doesn't work at all on your system but Esound is the preferred plugin as it works with ESD. ESD is gnome's sound server and it allows multiple applications to access the soundcard at once. This means that you can have gaim, xmms, gnome, and totem for example all using sound at the same time. 

You might need to change the output plugin on other multimedia programs:

If you use amarok you will notice that when amarok is playing no other applications can produce sound. You can fix this by right clicking on the amarok window, selecting "configure amarok". Then choose Engine and select the gstreamer sound system. Then change the output plugin from osssink to esdsink and hit apply & OK. 

rhythmbox should use esd by default with gstreamer. Xine and Totem should also be setup correctly as should gaim.

---

### Post by titus1950 on 2005-07-08
[QUOTE=Djeepy46234]Hi

When I try to play some music on ubuntu, it's not working. Sound is not working at all ...

I have a **Intel 82801FB ICH6 - Azalia Audio Controller**  audio card...

Someone help me please

Have a nice day :)[/QUOTE]


Hi, why don't you try this first,it worked for my Intel 82801FB ICH6: 
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)
and then:
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Have a nice day :)[/QUOTE]

---

### Post by Djeepy46234 on 2005-07-08
I already did this but for this part :

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

Each time i do this, the terminal say can't find or its a too old version...

---

### Post by titus1950 on 2005-07-08
[QUOTE=Djeepy46234]I already did this but for this part :

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

Each time i do this, the terminal say can't find or its a too old version...[/QUOTE]



Take a look at this I am not an advanced user but this is important to read...
[http://forums.fedoraforum.org/archive/index.php/t-30914.html](http://forums.fedoraforum.org/archive/index.php/t-30914.html)

---

### Post by Djeepy46234 on 2005-07-08
[QUOTE=titus1950]Take a look at this I am not an advanced user but this is important to read...
[http://forums.fedoraforum.org/archive/index.php/t-30914.html](http://forums.fedoraforum.org/archive/index.php/t-30914.html)[/QUOTE]
I don't understand this manipulation, I think this manipulation is not for my sound card and it's for fedora, no ?

When I type alsamixer, i get this :

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.8 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: Camera                                                                 &#9474;
&#9474; Chip: USB Mixer                                                              &#9474;
&#9474; View: Playback                                                               &#9474;
&#9474; Item: Auto Gain Control                                                      &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                                                              &#9474;
&#9474;                                  <Auto Gai>                                  &#9474;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

```
djeepy46234@ubuntu:~$ uname -rs
Linux 2.6.10-5-386
djeepy46234@ubuntu:~$ cat /proc/asound/cards
0 [Camera         ]: USB-Audio - Camera
                     Camera at usb-0000:00:1d.1-2, full speed
djeepy46234@ubuntu:~$

```

---

### Post by titus1950 on 2005-07-08
> **Djeepy46234]I don't understand this manipulation, I think this manipulation is not for my sound card and it's for fedora, no ?

When I type alsamixer, i get this :

```
&#9484 said:**
> &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: Camera                                                                 &#9474;
&#9474; Chip: USB Mixer                                                              &#9474;
&#9474; View: Playback                                                               &#9474;
&#9474; Item: Auto Gain Control                                                      &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                                                              &#9474;
&#9474;                                  <Auto Gai>                                  &#9474;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```
Yes but at the end there is this about alsa linux driver that helped in my case
(1.0.9rc3)Driver 

[http://www.alsa-project.org/](http://www.alsa-project.org/)

---

### Post by Djeepy46234 on 2005-07-10
It's still not working, also with you driver...

Another idea ?  :???:

---

