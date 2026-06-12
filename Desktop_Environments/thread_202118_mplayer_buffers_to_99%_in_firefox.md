---
title: "mplayer buffers to 99% in firefox"
date: 2006-06-22
forum: Desktop Environments
---

### Post by degel3030 on 2006-06-22
so i followed many tutorials and howtos and whatnot and i can not get trailers from apple.com/trailers to work properly, now when i go to watch a trailer it loads part way then kind of flashes, (like its suppose to and start playing, i had this working in fc5) then goes back to the loading screen and loads till 99% and doesnt do a thing
im thinking maybe i should reinstall everything or something, i dont know, if i could get some help that would be great cause i have had some decent success installing everything else
ive looked at others having the same problems but most just seem to be from either not installing the win32codec or running old software
aggrrr please any help would be very appreciated

---

### Post by will_in_wi on 2006-06-22
First, have you read the restricted formats page in the wiki? That would be the first place to look. Second, what plugin are you using in firefox? I am assuming you are using gnome.

---

### Post by degel3030 on 2006-06-22
yes i have read the restricted formats in wiki, im using mplayer for the plugin with the essential codecs and the win32 and yes on gnome

---

### Post by will_in_wi on 2006-06-22
[http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)
Here is the configuration information.

---

### Post by Anduu on 2006-06-22
Try right clicking the mplayer window in your browser and select configure.Try a different video output.

I do not have video overlay enabled in my xorg.conf so when the plugin tries to use xv it does that to me.If i set it to use gl it works fine.

---

### Post by degel3030 on 2006-06-22
ok so i did the config thing, and i dont know which video out to try
one thing is that when i tried to use mplayer running from command line i had an error with the sound, and if i got to system-preferences-sound the default sound is constantly on the wrong thing, it goes to some usb (i think web cam) driver and i change it back, still wont change back
also i just rebooted to the older kernel, read somewhere that helped but it didnt for me

---

### Post by Anduu on 2006-06-22
[QUOTE=degel3030]ok so i did the config thing, and i dont know which video out to try[/QUOTE]

Just try each one...be sure to close the page containing the video and reload it so mplayer will restart using the new settings.

One other thing...be sure to try different sites and different videos as sometimes a certain one will not work even if mplayer is configured correctly.

---

### Post by degel3030 on 2006-06-23
ok so just to be clear, you wanted me to have mplayer open, keep it open and change in the preferences the video driver and restart firefox each time correct....anyways nothing worked, but one thing i did notice is that i am not able to play any episodes of futurama that i have on my hard drive, here is my error


kdegel@ubuntu:~$ mplayer /media/hdc1/TV/cartoons/Futurama\ season\ 1-5\ \(complete\)\ +\ extras/Futurama\ Season\ 3\ \(complete\ DVDRip\)/Futurama\ -\ S03E05\ -\ Amazon\ women\ in\ the\ mood.avi
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /media/hdc1/TV/cartoons/Futurama season 1-5 (complete) + extras/Futurama Season 3 (complete DVDRip)/Futurama - S03E05 - Amazon women in the mood.avi.
AVI file format detected.
VIDEO:  [XVID]  576x432  16bpp  25.000 fps  989.7 kbps (120.8 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.la" failed
[AO ESD] latency: [server: 0.28s, net: 0.00s] (adjust 0.28s)
AO: [esd] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 576 x 432 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 576x432 => 576x432 Planar YV12
No bind found for key 'JOY_UP'-JOY_AXIS3_MINUS
X11 error: BadAlloc (insufficient resources for operation) ??,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by degel3030 on 2006-06-23
just to be clear, when i did that it opened mplayer up for just a split sec, heard just a sec of noise then it closed right away

---

### Post by degel3030 on 2006-06-23
holly #$%@ i fixed it, thank you so much for being so patient, so i installed the nvidia drivers but didnt comment out the dri, and i didnt change the driver from nv to nvidia
sorry for the time you guys spent answering and looking at this post, maybe someone in the future will make a stupid mistake as i did, thanks again

o also i had to change the mplayer settings to gl2 cause it was playing the video really really fast haha


EDIT: just to be clear these were in the /etc/X11/xorg.conf file that these changes needed to be made

---

### Post by arthur on 2006-06-23
*This is one of those places where you are bound to find some very patient (and helpful) people :) .*

---

