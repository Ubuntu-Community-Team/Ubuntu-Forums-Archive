---
title: "Why I installed GNOME to KDE?"
date: 2010-05-23
forum: Desktop Environments
---

### Post by erngab on 2010-05-23
[FONT=Verdana][SIZE=2]Kubuntu 10.04 x64[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]Everything is working OK (I think on audio and the graphics also)[/SIZE][/FONT][FONT=Verdana][SIZE=2]
 I lived peacefully, but then I decided ... [/SIZE][/FONT][FONT=Verdana][SIZE=2]install the GNOME environment on KDE.[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]    [FONT=Verdana][SIZE=2]When start KDE in KDE no sound (sometimes work sometimes not). When there is no sound log to GNOME "unmute" sound in GNOME and in GNOME work everything is OK. Log back to KDE sound works in KDE ([/SIZE][/FONT][FONT=Verdana][SIZE=2]i[/SIZE][/FONT][FONT=Verdana][SIZE=2]n most cases).[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]I[/SIZE][/FONT][FONT=Verdana][SIZE=2]t seems to me that in GNOME has been constantly sound (start, restart, logout).[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]GNOME [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Sound Preferences[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2] ** Hardwer
 - Internal Audio 1Output / 1 Input Analog Stereo Duplex
 - Radeon HD 3870 Audio device 1 Output Digital Stereo (HDMI) Output[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2] ** Output
 - Internal Audio Analog Stereo (Chosen this)
 - Radeon HD 3870 Audio device Digital Stereo (HDMI)

KDE[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Sound and Video Configuration
 ** Audio Output 
 - HDA Intel (AD198x Analog)
 - Playback-recording through the PulseAudio sound server
 - HDA ATI HDMI, ATI HDMI (HDMI Audio Output)[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2] - Jack Audio Connectio Kit
 - Esound (ESD)[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]I[/SIZE][/FONT][FONT=Verdana][SIZE=2] must mention that the graphics in KDE [/SIZE][/FONT][FONT=Verdana][SIZE=2]faltering after installing GNOME. E[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]rror often occurs when changing from Gnome to KDE.[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Logout does not work quite right [/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]-[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000] does not appear.[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]D[/SIZE][/FONT][FONT=Verdana][SIZE=2]oes the environment affect each other GNOME KDE?[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2][COLOR=#000000]W[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]hat is the problem?[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
 Is there some solution?[/SIZE][/FONT]

---

### Post by nikhilbhardwaj on 2010-05-23
do you have pulseaudio installed
in my case its generally the one causing all the problems

---

### Post by erngab on 2010-05-23
[SIZE=2]Before  I instalisao GNOME environment everything was fine.
In KDE it all  works well. 
Now in KDE - neither audio and video are not good. 
In the GNOME environment everything is OK.[/SIZE]

---

### Post by lovinglinux on 2010-05-23
[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

---

### Post by erngab on 2010-05-23
[FONT=Verdana][SIZE=2]> **lovinglinux said:**
> [http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

[/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Is not entirely clear to me  what I do with code. I put  it in the terminal in Kubuntu.
I  would like to keep the GNOME environment - I do not want to remove it.
In the terminal  I got
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.32-21 is not installed, so not removed
Package linux-headers-2.6.32-21-generic is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  install-package: Depends: gdebi-kde but it is not going to be installed
  kdebase-runtime: Depends: phonon-backend-xine but it is not going to be installed or
                            phonon-backend
  kubuntu-debug-installer: Depends: kpackagekit but it is not going to be installed
  libkopete4: Depends: kopete but it is not going to be installed
E: Broken packages

```[/SIZE][/FONT]

---

### Post by 3Miro on 2010-05-23
KDE and Gnome use different sound schemes and this is probably causing a conflict. What I have done in the past was:
```
sudo alsa --force-reload
```

Now I just ditch both KDE and Gnome and use XFCE.

---

### Post by lovinglinux on 2010-05-23
> **erngab said:**
> [FONT=Verdana][SIZE=2]

[/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Is not entirely clear to me  what I do with code. I put  it in the terminal in Kubuntu.
I  would like to keep the GNOME environment - I do not want to remove it.

That command is to remove gnome. So, better try to fix the sound issues.

---

### Post by erngab on 2010-05-23
[FONT=Verdana][SIZE=2][COLOR=#000000]Resolved problem with  the help of instructions from the address 
[/COLOR][/SIZE][/FONT][SIZE=2][[FONT=Verdana]**Jaunty 9.04 Sound Solutions**[/FONT]]("http://ubuntuforums.org/showthread.php?t=1130384")
[/SIZE][SIZE=2][/SIZE]
[SIZE=2]Thanks for your help.
[/SIZE]

---

