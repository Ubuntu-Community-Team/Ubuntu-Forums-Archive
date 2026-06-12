---
title: "Problems with Ubuntu on Dell XPS17"
date: 2010-12-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arpoodle on 2010-12-04
I've just finished installing Ubuntu 10.04 on my new Dell XPS 17 laptop.

I've hit upon some issues, some I've resolved, some not.

Video: the install as it is, resorts to 800x600 with no options to improve the resolution.

There's no drivers available for the Nvidia GT445 video card that's installed in this, however, the 64bit driver for the GT435 seems to work fine.

Sound: I've got no sound, and no obvious reason why not.

Some system info as follows:

> root@hiro:~# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0c00000 irq 22
root@hiro:~# cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ID 665
root@hiro:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
root@hiro:~# aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
root@hiro:~# uname -a
Linux hiro 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux
root@hiro:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid
Any ideas?

---

### Post by arpoodle on 2010-12-06
Installed the realtek drivers, and it works.. funnily enough :)

Seem to have problems with the HDMI output tho, as it's not being detected and so my second display is useless.

It's not showing up in the Nvidia settings app.

Does anyone know if the GT435 video card has HDMI support; it could be that the GT435 doesn't have it, but the GT445 does.

Or am I missing something?

Xrandr shows the following:
> Screen 0: minimum 320 x 175, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 0mm x 0mm
   1600x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0     55.0     56.0     57.0     58.0  
   960x600        59.0  
   960x540        60.0  
   840x525        61.0     62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0     72.0     73.0  
   800x512        74.0  
   720x450        75.0  
   720x400        76.0  
   700x525        77.0     78.0     79.0     80.0  
   680x384        81.0     82.0  
   640x512        83.0     84.0     85.0  
   640x480        86.0     87.0     88.0     89.0     90.0     91.0  
   640x400        92.0  
   640x350        93.0  
   576x432        94.0     95.0     96.0     97.0     98.0     99.0    100.0  
   512x384       101.0    102.0    103.0    104.0    105.0  
   416x312       106.0  
   400x300       107.0    108.0    109.0    110.0    111.0  
   360x200       112.0  
   320x240       113.0    114.0    115.0    116.0  
   320x200       117.0  
   320x175       118.0  



---

### Post by psnel on 2011-01-29
arpoodle continues this thread with solution here:
(Re: **Nvidia GT445 on 64bit**)
[http://ubuntuforums.org/showthread.php?p=10406422]("http://ubuntuforums.org/showthread.php?p=10406422")

---

