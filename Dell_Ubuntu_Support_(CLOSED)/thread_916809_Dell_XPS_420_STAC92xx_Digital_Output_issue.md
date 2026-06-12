---
title: "Dell XPS 420 STAC92xx Digital Output issue"
date: 2008-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SpearZ on 2008-09-11
Hi all,
Firstly, I apologise for my lack of knowledge of Ubuntu.  I'm a long time Windows user, dual booting to Ubuntu 8.04 so that I can get used to it and switch over permanently.  I've run previous version of Ubuntu and I have to say this version is a massive leap with regards to hardware compatability (the ATI drivers 'just work' now?! :-D  I had lots of problems with them in the past).  However..... my only issue now seems to be after installing Hardy, I can't get any sound outputting via my soundcard's digital output.
As I said, I'm dual booting with Windows and I can playback audio via the digital output with no problems...but in Ubuntu, I just can't get it to output.
I've looked at lots of threads and I'm going round in circles ;-(

My machine is a Dell XPS 420 with the STAC92xx integrated sound.
-If I take a look in System->Preferences->Sound, the devices listed are
STAC92xx Digital
STAC82xx Analog
ATI HDMI
ALSA
OSS
PulseAudio Sound Server
...selecting each of them and clicking 'test', produces no sound

-If I open my volume control, file->change device->
..I see
0: HDA Intel (Alsa mixer)
1: HDA ATI HDMI (Alsa mixer)
2: Sigmatel STAC9227 (OSS mixer)
3: Playback: ALSA PCM on front:0 (STAC92xx Analog)
4: Capture: Monitor Source of ALSA PCM on front:0
5: Capture: ALSA PCM on front:0

-If I run aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




Can anyone help?  Have I simply got something set wrong, or is there a hardware issue?

Thanks a lot in advance, it's stopping me from using Ubuntu and I'm at a complete loss as to how to proceed.

---

### Post by SpearZ on 2008-09-11
Got it after another hour of clicking around!
Under Volume Control, File->Change Device-> 2: Sigmatel STAC9227 (OSS mixer)
Edit->Preferences
Digital-1

...turn up the volume ;-)

Wow that had me stumped for a while!
Doh.

At least 'everything' seems to be working now.  I am *very* happy ;-)
Cheers,

---

### Post by chrwes on 2008-09-16
Thanks for the help. :) I also been fiddeling around for hours with this issue!

---

### Post by SpearZ on 2008-09-16
Hey, no problem.  Seems to work absolutely fine now, except I can't seem to play two audio streams at the same time.
For example, playing an .avi with mplayer and opening a youtube video.  The first stream you open seems to 'hog' the audio device until you close it.

Although I don't actually watch youtube videos at the same time as watching avi files, it's a bit of a pain, especially as compiz allows for multiple desktops.

Do you experience the same thing chrwes?
I wonder if it's just Digital Audio devices?  Please let me know if you experience the same thing!

Cheers,

---

### Post by JacobVF on 2008-10-11
Thanks for the help, tried to get it to work on my XPS210 and it was the same solution :)

---

### Post by lwb1086y on 2008-10-11
[size=2]wow,nice yeeeeehhhhhhhhhhhaaaaaaaaaaa[/size]------------------------------------------------------------------------------------------------------------------------------[img]http://www.qzone.la/img/userup/0808/2GU30U016.jpg[/img]our wow power leveling site:buy [wow power leveling](http://www.toppowerlevel.net/),[wow powerleveling](http://www.yoyo-power-leveling.com/),rapid [world of warcraft power leveling](http://www.yoyo-power-leveling.com/),[world of warcraft powerleveling](http://www.wow-powerleveler.com/),buy [wow gold](http://www.wow-power-leveling1.com/buy_wow_gold.php)

---

