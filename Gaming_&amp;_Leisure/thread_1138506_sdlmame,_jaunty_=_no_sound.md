---
title: "sdlmame, jaunty = no sound"
date: 2009-04-26
forum: Gaming &amp; Leisure
---

### Post by talz13 on 2009-04-26
Edit: I was able to get some sound out of sdlmame after following part A of the guide at:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
I will post back if I continue having any issues...






Hey, I just installed Jaunty the other day and was pleased to see that my ATi card works pretty well with it now.  I want to get mame running on here so I don't have to dual boot to windows to play, but as it is right now, I get no sound out of mame at all.

I have tried changing my Sound preferences to ALSA from pulse (and back again after it didn't fix the problem).  I have tried sdlmame from the repositories (0.129 i believe), and have replaced it with 0.130u4 from [http://wallyweek.altervista.org/](http://wallyweek.altervista.org/) but still no sound...

My system is:
Intel Q6600
ATi HD 4870
4gb ram
2x1tb raid 1
Gigabyte GA-EP45-DS3L using onboard audio

---

### Post by bobince on 2009-05-07
libsdl1.2debian-pulseaudio (from universe) is the critical package. The -alsa sound just clicks and farts for me, even if Pulse is not using the device.

---

### Post by JMac82 on 2009-07-30
yep, right on.  that package is what's needed.

---

### Post by chuckyp on 2009-08-26
I'm also trying to get sdlmame working with a bare bones system.
Basically what i've done.

I installed a command line system, then I installed Xorg and nvidia drivers. I have X working and everything else; however, I can not get sound through sdlmame. I've tried various fixes suggested including installing libsdl1.2debian-all libsdl1.2debian-pulseaudio etc... switching back and forth.  Nothing is muted at this time and sound works in other applications.

The only way I was able to get sound working in sdlmame at one point was to install the ubuntu-desktop package and all the gnome garbage that I don't want on the cabinet. I then installed libsdl1.2debian-all and it started working.

I would like to get sound working without having gnome and all the extras installed as this machine will be a strictly in a cabinet. I'm at a loss i've tried about everything I can think of and I'm looking for suggestions.

Edit: Sorry for hijacking your thread I will post a new one.

---

### Post by williamts99 on 2009-10-24
> **bobince said:**
> libsdl1.2debian-pulseaudio (from universe) is the critical package. The -alsa sound just clicks and farts for me, even if Pulse is not using the device.

This was my exact problem also, libsdl1.2debian-pulseaudio

sudo apt-get install libsdl1.2debian-pulseaudio

Fixed it perfectly for me.

Best Regards,
Williamts99

---

### Post by biodiesel-bri on 2009-11-01
Sound under sdlmame was working for me in 9.04 but when I upgraded to 9.10 sdlmame sound stopped working.  I ran the same command, apt-get complained but sound is again working for me.

```

sudo apt-get install libsdl1.2debian-pulseaudio
Reading package lists... Done                                             
Building dependency tree                                                  
Reading state information... Done                                         
The following packages were automatically installed and are no longer required:
  libdbus-qt-1-1c2                                                             
Use 'apt-get autoremove' to remove them.                                       
The following packages will be REMOVED:
  libsdl1.2debian-alsa
The following NEW packages will be installed:
  libsdl1.2debian-pulseaudio
0 upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 211kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com karmic/universe libsdl1.2debian-pulseaudio 1.2.13-4ubuntu4 [211kB]
Fetched 211kB in 1s (133kB/s)
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you requested:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-4ubuntu4) | libsdl1.2debian-all (= 1.2.13-4ubuntu4) | libsdl1.2debian-esd (= 1.2.13-4ubuntu4) | libsdl1.2debian-oss (= 1.2.13-4ubuntu4) | libsdl1.2debian-nas (= 1.2.13-4ubuntu4) | libsdl1.2debian-pulseaudio (= 1.2.13-4ubuntu4); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 290154 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libsdl1.2debian-pulseaudio.
(Reading database ... 290146 files and directories currently installed.)
Unpacking libsdl1.2debian-pulseaudio (from .../libsdl1.2debian-pulseaudio_1.2.13-4ubuntu4_amd64.deb) ...
Setting up libsdl1.2debian-pulseaudio (1.2.13-4ubuntu4) ...

```

---

