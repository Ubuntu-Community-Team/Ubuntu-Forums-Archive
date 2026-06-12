---
title: "HDMI Audio not working on XPS M1530 - Hardy"
date: 2008-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by steenbras on 2008-05-10
I found a thread in the archive [here]("http://ubuntuforums.org/showthread.php?p=4844602") but can't find any follow up to it. I've got an XPS M1530 and HDMI video is fine, but audio doesn't work. Sound comes from the laptop. If I try to redirect sound to STAC92xx Digital using Preferences/Sound it just mutes all audio.

I really would like to get this working - all audio out of my laptop to my AV amp can only come out as stereo. John from Dell on the other thread said that Dell are actively working on this and hope to have a resolution in Hardy, but looks like it didn't make it. Please help?

---

### Post by steenbras on 2008-05-16
Does Dell monitor these forums? It would appear not. :(

---

### Post by Trollslayer on 2008-05-27
> **steenbras said:**
> I found a thread in the archive [here]("http://ubuntuforums.org/showthread.php?p=4844602") but can't find any follow up to it. I've got an XPS M1530 and HDMI video is fine, but audio doesn't work. Sound comes from the laptop. If I try to redirect sound to STAC92xx Digital using Preferences/Sound it just mutes all audio.

I really would like to get this working - all audio out of my laptop to my AV amp can only come out as stereo. John from Dell on the other thread said that Dell are actively working on this and hope to have a resolution in Hardy, but looks like it didn't make it. Please help?

I had the same problem on an Abit motherboard.
First, does aplay -l list the HDMI port?
Second, have you installed the default sound card selector for ALSA (asoundconf-gtk) and used that to set HDMI as the default output?
If so, when you run 'alsamixer' it should show the HDMI output which is muted initally, just enable that.

Hope this helps.

---

### Post by steenbras on 2008-05-28
Thanks trollslayer - what you're posting sounds hopeful.

Unfortunately, aplay -l shows nothing looking like an HDMI port. This is the output I get:
```
miker:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Have installed asoundconf and here's my output of the list command:
```
-miker:~$ asoundconf list
Names of available sound cards:
Intel

```

Why would the HDMI port not be picked up?

---

### Post by Trollslayer on 2008-05-28
The STAC92xx is the actual audio chip, check the ALSA project wiki to see how much support there is for it:
[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)
It was only in 1.0.14 that HDMI support for the Realtek ALC883 on my Abit motherboard was added.
Must admit, I've been in electronics and PCs for a long time and haven't dealt with that type of part before.

Ah, it looks like a Philip/NXP part, they aren't that helpful in releasing data for open source drivers.

---

### Post by mazy on 2008-05-31
DELL XPS1330 Hardy 8.04
---

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but

aplay -D hw:0,1 Prelude.wav
produces no  sound at all
(HDMI -> Denon AVR2307)

---

### Post by Trollslayer on 2008-05-31
Does your motherboard ahve a digital output? Optical or coax that is.
If so, this is where the second outpuut is going.
Have you checked to see if the output is muted?

---

### Post by mazy on 2008-06-03
sure. AV-Receiver is unmuted - i've switch HDMI cable from DVD Player to notebook. 

iec958 is un-muted

[http://ubuntuforums.org/showthread.php?t=813454&highlight=HDMI+sound](http://ubuntuforums.org/showthread.php?t=813454&highlight=HDMI+sound)

](*,)

BTW.
[http://ubuntuforums.org/showpost.php?p=2871959&postcount=9](http://ubuntuforums.org/showpost.php?p=2871959&postcount=9)

> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0


i haven't "card 1" in aplay -l 
alsa 1.0.16
...

---

### Post by mazy on 2008-06-05
[http://xbmc.org/forum/showpost.php?p=184563&postcount=4](http://xbmc.org/forum/showpost.php?p=184563&postcount=4)
> 
Audio over HDMI is not supported with any nvidia cards at the current time. Nvidia says wait for the 177.xx version and maybe.
sad.

---

### Post by mazy on 2008-06-07
> **mazy said:**
> [http://xbmc.org/forum/showpost.php?p=184563&postcount=4](http://xbmc.org/forum/showpost.php?p=184563&postcount=4)

sad.

IT WORKS. 
I've did it!
XPS 1330
Hardy 8.04
1. updated BIOS from A09 to A10 revision
2. apt-get remove nvidia-glx-new (169)
3. download from nvidia fresh drivers - 173 and install
4. setted up twinview (AV receiver mute sound without video)
5. Sound -> changed from auto to STAC92xx Digital
6. pressed 'Test' and IT WORKS !!!

---

### Post by steenbras on 2008-06-08
Aaargggghhhh - got my hopes up there. As mine's a 1530, and I can't see an upgrade to my version of the BIOS, I followed your instructions from step 2 onwards. Or rather - got to the end of step 3, and have now completely lost Nvidia. I can't even revert to the older version - 169. I'd love to get this 173 version working though... perhaps the HDMI audio will work with 173.

So how can I get Nvidia to load? The install worked, apparently, but I can't get above low-graphics mode using the nvidia device in my xorg.conf, and nvidia-settings tells me that I don't have the nvidia drivers installed. I've also now lost the entry in the restricted drivers screen.

---

### Post by mazy on 2008-06-09
> **steenbras said:**
> and have now completely lost Nvidia. I can't even revert to the older version - 169. I'd love to get this 173 version working though... 
So how can I get Nvidia to load? The install worked, apparently, but I can't get above low-graphics mode using the nvidia device in my xorg.conf, and nvidia-settings tells me that I don't have the nvidia drivers installed. I've also now lost the entry in the restricted drivers screen.
i've got the same problem but solved it:


sudo aptitude install linux-headers-`uname -r` build-essential xserver-xorg-dev

cat /etc/default/linux-restricted-modules-common :
DISABLED_MODULES="nv nvidia_new"
-- modules SHOULD be disabled for working with custom 173 driver
sudo /etc/init.d/gdm stop
sudo -s -H 
sh NVIDIA-Linux-XXX-X.X-XXX-pkg1.run 

install will ask to run 'nvidia-xonfig' - press NO.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
----
Section "Device" 
        Identifier      "NVIDIA Corporation"
        Driver          "nvidia"
        Option          "NoLogo" "TRUE"
        BusID           "PCI:1:0:0"
EndSection

Section "Module" 
        Load    "i2c"
        Load    "glx"
EndSection

-+---
sudo /etc/init.d/gdm start
after run
sudo nvidia-settings

---

### Post by steenbras on 2008-06-09
I found another post that got it working just fine - I think that there's more to remove than just nvidia-glx-new. Doing an apt-get remove --purge nvidia* worked for me.

Now I've got 173 running :D but no STAC92xx Digital in aplay -l :(

---

### Post by dagurb on 2008-06-26
> **steenbras said:**
> I found another post that got it working just fine - I think that there's more to remove than just nvidia-glx-new. Doing an apt-get remove --purge nvidia* worked for me.

Now I've got 173 running :D but no STAC92xx Digital in aplay -l :(

Could you provide a link to the thread that you found? Or an explanation of what you did?

---

### Post by jvcastle on 2008-07-01
Without doing anything (on Hardy 8.04, .19 kernel), I've got "Stac92xx Digital" (as well as analog) from "aplay" -l, but don't see the HDMI anywhere else.  As a note, I don't have sound from Vista on this same machine (though in a way I was less surpised...)

---

### Post by sdennie on 2008-07-03
With an XPS m1330 with A11 BIOS, vanilla 2.6.24.7 kernel, NVidia driver 173.14.09 and ALSA 1.17rc3, this works flawlessly.  If you have the Digital device in "aplay -l", the key seems to be opening the Volume Control applet and going to Edit->Preferences and enabling IEC958.  Then, in the Switches tab, check that box.  When you switch to HDMI using Fn-F8, you should get sound without having to configure anything else but, the laptop sound will also play (can be muted for me by muting the "Front" channel).  When I just tried this, the sound was terrible until I upgraded to ALSA 1.17rc3.  Also note that I don't use pulse audio at all, just straight ALSA.

---

### Post by Rayman2200 on 2008-07-04
Last week i played with the HDMI out and i could play video and sound over the HDMI out of my M1330. This works out-of-the-box with the restricted driver from ubuntu. Problem is, i forgot the settings i made :(

yesterday i try it a secound one and it failes :( don't know why

i can test it today a third time, hope i can hear something with the out-of-the-box config and can tell you guys whats the correct config for the sound.

---

### Post by raphoun on 2008-07-24
> **vor said:**
> With an XPS m1330 with A11 BIOS, vanilla 2.6.24.7 kernel, NVidia driver 173.14.09 and ALSA 1.17rc3, this works flawlessly.  If you have the Digital device in "aplay -l", the key seems to be opening the Volume Control applet and going to Edit->Preferences and enabling IEC958.  Then, in the Switches tab, check that box.  When you switch to HDMI using Fn-F8, you should get sound without having to configure anything else but, the laptop sound will also play (can be muted for me by muting the "Front" channel).  When I just tried this, the sound was terrible until I upgraded to ALSA 1.17rc3.  Also note that I don't use pulse audio at all, just straight ALSA.


Works with my m1530 and ubuntu 8.04, tanks so much !

---

### Post by carlosbertholdi on 2008-10-07
> **steenbras said:**
> Thanks trollslayer - what you're posting sounds hopeful.

Unfortunately, aplay -l shows nothing looking like an HDMI port. This is the output I get:
```
miker:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Have installed asoundconf and here's my output of the list command:
```
-miker:~$ asoundconf list
Names of available sound cards:
Intel

```

Why would the HDMI port not be picked up?

Finally, I found someone with the same problem as mine.

I have an asus g1s, aplay -l doesn't mention anything about hdmi or digital audio or S/PDIF the only that mention an "IEC958 (S/PDIF) Digital Audio Output" is with an aplay -L, here's my aplay -l:

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and aplay -L:

> default:CARD=Intel
    HDA Intel, ALC660-VD Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


As you can see there is an IEC958, but I can't find it on the mixers to unmuted.

and here "asoundconf list":

> carlos@g1s:~$ asoundconf list
Names of available sound cards:
Intel


---

### Post by carlosbertholdi on 2008-10-07
> **steenbras said:**
> Aaargggghhhh - got my hopes up there. As mine's a 1530, and I can't see an upgrade to my version of the BIOS, I followed your instructions from step 2 onwards. Or rather - got to the end of step 3, and have now completely lost Nvidia. I can't even revert to the older version - 169. I'd love to get this 173 version working though... perhaps the HDMI audio will work with 173.

So how can I get Nvidia to load? The install worked, apparently, but I can't get above low-graphics mode using the nvidia device in my xorg.conf, and nvidia-settings tells me that I don't have the nvidia drivers installed. I've also now lost the entry in the restricted drivers screen.

You need to delete the following files after that nvidia drivers will load, I had had the same problem:

> /etc/init.d/nvidia-glx

/etc/init.d/nvidia-kernel

/lib/linux-restricted-modules/.nvidia_new_installed

Read more [here]("http://www.nvnews.net/vbulletin/showthread.php?t=72490").

---

### Post by carlosbertholdi on 2008-10-07
> **steenbras said:**
> I found another post that got it working just fine - I think that there's more to remove than just nvidia-glx-new. Doing an apt-get remove --purge nvidia* worked for me.

Now I've got 173 running :D but no STAC92xx Digital in aplay -l :(

I had the same problem as you, below how I solved it:

Finally, I did, I made hdmi sound work on my asus g1s.

Now my aplay -l shows a digital device:
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC660-VD Digital [ALC660-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I made it work by going to this file "/etc/modprobe.d/alsa-base":
> sudo gedit /etc/modprobe.d/alsa-base

then I delete all the contents of that file and put this:
> options snd-hda-intel index=0 model=3stack-660-digout

at "model" you have to put one that is made for your hardware, look [here]("http://ubuntuforums.org/showpost.php?p=5131958&postcount=2") for a complete list of models available.

Then I use alsamixer to unmuted the IEC958.

Now, I have crisp sound on Linux.

---

