---
title: "amarok not playing music on ubuntu 9.04"
date: 2009-05-14
forum: General Help
---

### Post by arvsr1988 on 2009-05-14
My amarok 2.0 is not playing music. when i open it the following message displays on the top right corner of the screen:

" The audio playback device HDA Intel (Connexant Analog) does not work. Failing back to default."

My audio playback device as set in the sound preferences (system) is ALSA. If i set the device to Connexant Analog and test it doesn't work here too. 

Whats the solution around this problem? How can i change the audio playback device on amarok?

---

### Post by cottfcfan on 2009-05-14
Make sure that in Synaptic you have "libxine1-ffmpeg"
installed.
That worked for me.

---

### Post by arvsr1988 on 2009-06-08
already have it installed.. any other solutions?

---

### Post by keithclark on 2009-06-19
> **cottfcfan said:**
> Make sure that in Synaptic you have "libxine1-ffmpeg"
installed.
That worked for me.

It also worked for me, thanks.  Appreciated!

Keith

---

### Post by arvsr1988 on 2009-06-20
pls give me another solution.. i have this package installed.

---

### Post by 0x29a on 2009-06-20
There has been a problem with Conextant audio in the past, apparently.

Some of the things I would ask is has music every worked? If so, when did amarok stop playing music? What happened before it stopped playing music? What changed before it stopped playing music? What type of computer are you trying to get music to play on? Do you get sosund when you use OSS?

Were you tinkering with ALSA at all? I couldn't get sound out of anything after tinkering with .asoundrc. Once I deleted that file things started working again.

Also, please post the output of```

cat /proc/asound/oss/sndstat
```
and:```

sudo lspci
```

---

### Post by 0x29a on 2009-06-20
I forgot to mention how to change audio devices in Amarok. Sorry. On the menubar, go to:

Settings > Configure Amarok > Engine

Set Output pugin to Autodetect

---

### Post by arvsr1988 on 2009-06-22
hey, i haven't been tinkering with my .asoundrc. infact i couldn't even find the file in my system. 

i was using amarok in ubuntu 7.1, 8.04 and 8.10 without any problems but once i upgraded to ubuntu 9.04, i've been having playback problems. It hasn't even played music once. However Rhythmbox, banshee and the others all work for me. 

below is the output of the codes you asked for. 
[B]
arvind@arvind-laptop:~$ cat /proc/asound/oss/sndstat[/B]
Sound Driver:3.8.1a-980706 (ALSA v1.0.18rc3 emulation code)
Kernel: Linux arvind-laptop 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686
Config options: 0
Installed drivers: 
Type 10: ALSA emulation
Card config: 
HDA Intel at 0xd0340000 irq 22
Audio devices:
0: CONEXANT Analog (DUPLEX)
Synth devices: NOT ENABLED IN CONFIG
Midi devices: NOT ENABLED IN CONFIG
Timers:
31: system timer
Mixers:
0: Conexant CX20551 (Waikiki)

**sudo lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

by the way i'm using amarok 2.0.2 on kde 4.2.2 and there is no engine configuration under the menu you told me.  Pls suggest solutions. Thanks.

---

### Post by pakkispower on 2009-06-30
I was having the same problem, really getting on my nerves. well i got it working! followed the instructions from here: [http://mcguyverofbeer.com/?p=284]("http://mcguyverofbeer.com/?p=284") Hope it helps!

---

### Post by Edwardgemini on 2009-07-20
> **cottfcfan said:**
> Make sure that in Synaptic you have "libxine1-ffmpeg"
installed.
That worked for me.

 Worked perfectly for me! Thanks! It was becoming a headache. :D

---

### Post by GeekGirl1 on 2009-07-21
I'm using Gnome 2.26.1 with amarok 2.02. Add another thank you for "libxine1-ffmpeg".

It also seemed to need Pulse Audio (install pulseaudio in Synaptic) and the instructions from pakkispower's link:

sudo apt-get install phonon-backend-xine
sudo apt-get remove phonon-backend-gstreamer

I have no idea why, but amarok is dependent on KDE's Oxygen cursor theme. You can't remove the cursor theme without removing amarok. :confused:

There's a transparent rectangle on my display when amarok is running. :???:

---

### Post by chinmaya_n on 2009-10-29
Installing "libxine1-ffmpeg" worked for me !!
Thanx

---

### Post by vikram0460 on 2009-12-17
thank you 
it is worked for me also

---

### Post by jflaker on 2010-01-02
Yep, worked....Installed this earlier but I reloaded recently

---

### Post by designeru on 2010-01-24
> **cottfcfan said:**
> Make sure that in Synaptic you have "libxine1-ffmpeg"
installed.
That worked for me.

worked for me too... thanks :)

---

### Post by cleopete on 2010-02-23
> **cottfcfan said:**
> Make sure that in Synaptic you have "libxine1-ffmpeg"
installed.
That worked for me.

Worked for me too, but I didn't realize it right away-  if Amarok is open when you install the package, you'll have to restart it before it will work (Amaraok, not the comp).

My symptoms were a little different from the first poster.  I got no error messages. It would simply display the song info in the OSD for half a sec, then stop.  

I'm running this on a Macbook Pro with the Cirrus audio.  Amarok 2 options are listed under Settings -- Configure Amarok -- Playback -- Sound System Configuration button.  My rig shows 2 entries for HDA Nvidia (Cirrus Analog and Digital) which don't work.  I moved Pulse Audio up the list, though I suspect it would have defaulted to that on it's own.

There is a test button to check to see if that audio device works.

---

### Post by domino1241 on 2010-03-30
> **cottfcfan said:**
> Make sure that in Synaptic you have "libxine1-ffmpeg"
installed.
That worked for me.

Worked for me, too.  Big pimpin' playa.

---

### Post by MrJackdaw on 2010-05-02
Another person it worked for! Thanks!

---

### Post by PrototypeAlex on 2010-05-22
> **cottfcfan said:**
> Make sure that in Synaptic you have "libxine1-ffmpeg"
installed.
That worked for me.

Cheers, also works in Lucid.

---

