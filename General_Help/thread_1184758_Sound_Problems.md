---
title: "Sound Problems"
date: 2009-06-11
forum: General Help
---

### Post by Lyuokdea on 2009-06-11
I have a built in Realtex ALC 883 soundcard and am running Jaunty. I currently have OSS - Open Sound System working, but it only works for one device at a time (i.e. if I'm playing music, then Gaim won't make any sounds, and if i want to switch over and watch a youtube video with sound, i need to close both programs and then reopen firefox)

I have both Alsa and Pulseaudio installed. Alsa won't play at all, giving an error "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback." when I attempt to play the test sound from the sound preferences tab.

Pulseaudio gives every indication that it is playing (in the pulseaudio server menu), but no sound comes out. There are no error messages. However, it lists "no network device found" on the Default Server part of the device manager (i have it set to default). 

I also have the following devices listed on my sound card:

3 copies of HDA Intel ALC883 Analog (OSS) (2 of these will play the test sound, one will not)
a copy of HDA Intel ALC883 Analog (ALSA), which gives the same error message
HDA Intel ALC883 Digital (ALSA) - which won't give an error message, but will have no sound come out
Autodetect fails to play a sound, with no error message



Does anybody know of a good way to fix this? It's getting very annoying.

Thanks,

~Lyuokdea

---

### Post by gradinaruvasile on 2009-06-11
Remove pulseaudio. Kill the process with 
killall pulseaudio
in the terminal.
Edit the /etc/pulse/client.conf file with

sudo gedit /etc/pulse/client.conf 
in a terminal (give your password when asked)

look for 
autospawn = yes
change it to 
autospawn = no
Save the file

Kill the pulseaudio process with 
killall pulseaudio
in the terminal.

Set every device to ALSA in Sound Properties (system->properties->sound)

Open System->Preferences->Startup Programs (or Sessions, whichever you have)

click on add
name: kill pulseaudio
command: killall pulseaudio 
click add
close 
reboot

After rebooting check the sound levels.

---

### Post by Lyuokdea on 2009-06-11
still the same problem I used to have with ALSA, an error message pops up whenever i try to play the test sound:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I had an error message like this before I installed pulseaudio (i was trying to find another working sound manager), so there seems to be some problem with the alsa configuration

~Lyuokdea

---

### Post by Lyuokdea on 2009-06-11
Well, it alsa is now working with the exact same problem as before...it only plays sound from one source at a time. However, I still get the same error while trying to run a test sound through the system.

When I load ALSA Mixer, it correctly identifies the sound card as a Realtek ALC883, so that doesn't seem to be an issue, all the volumes are turned up

~Lyuokdea

---

### Post by Lyuokdea on 2009-06-11
Is there anyway to completely reinstall the sound drivers or something, and see if that fixes the problem? There doesn't seem to be any reason why this setup wouldn't work.

Thanks,

~Lyuokdea

---

### Post by Lyuokdea on 2009-06-11
Got it! Had to reconfigure PulseAudio, manually insert the .conf file into /etc/, and then get it to recognize the sound sync correctly

Thanks!,

~Lyuokdea

---

### Post by LostAngelino on 2009-06-19
Hello My sound issue is a little strange. Ive installed ubuntu 9.04 on my Toshiba Satillite L25-S1217. For about a week I searched this forum but theres nothing i can find that addresses my issue.  Basically i boot up open up my music player(or video player) i can listen for about five minutes then all of a sudden the sound crashes. it bascally sounds like it gets stuck then it stops and my audio stops working completely. happens with video as well. with video the sound crashes and then the video plays at a supre slow frame rate and becomes unviewable.  Happens online as well when watching videos. If a reboot the computer the sounds works again but again after five minutes sound crashes

Here is what lspci shows

```

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```

Hope theres a fix for this.

Thanks

---

