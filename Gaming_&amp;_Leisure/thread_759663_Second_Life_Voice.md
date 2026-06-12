---
title: "Second Life Voice"
date: 2008-04-19
forum: Gaming &amp; Leisure
---

### Post by Dekafox on 2008-04-19
I'm trying to set up Second Life's voice client on 1.19.1 and running into some issues.  I'm running the 8.04 RC x86_64.

First, regular sounds work fine, so that's not an issue.  I swapped the libopenal.so.1 library for the one from 1.19.0, as apparently there is a known issue with the one on 1.19.1.  After I do however, the dropdowns within the SL voice configuration box don't show anything except what I last set with the 19.1 library used.

When I log in, I only see myself listed in the list of active speakers.  With the 19.1 library I encounter the known issue of it constantly reconnecting every minute or so.  With the 19.0 library it doesn't reconnect, but I still don't see anyone else in the active speakers other than myself.

.openalrc is currently set to the following:
(define devices '(alsa))
#(define alsa-out-device "default")
(define alsa-in-device "plughw:0,0")
(define alsa-out-device "hw:0,0")

when I run aplay -l and arecord -l I see:
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

**** List of CAPTURE Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 1: Intel ICH - MIC ADC [NVidia CK8S - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any ideas on what to do to get it working?

*edit* 
I changed the openalrc to:
(define devices '(alsa))
#(define alsa-out-device "default")
(define alsa-in-device "plughw:0,0")
(define alsa-out-device "hw:0,0")

And copied over the SLVoice executable from 1.19.0 and now I connect and see people on the list if they're under 50m away, but when they talk I see the lines but hear nothing. I also saw lines when I tapped my mike so it's transmitting too. I've got the volume on the alsamixer all the way up on Mic but it doesn't pick anything up if it's beyond a couple mm it seems, but that's a seperate issue.

---

### Post by Dekafox on 2008-04-26
*bump*  Anyone?  

Also, when I tried using Wine to run the Windows version of the Voice stuff with the Linux client, I got this:

ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

Isn't dmix supposed to mix stuff, and not refuse connections?

*edit* Nevermind, got it working with Pulseaudio

---

### Post by Cheehwa Palen on 2008-05-30
Hi,

I tried this method as well by loading latest wine software and then attempting to run the windows client of sl. While successful in running it my sound comes thru my laptop speakers and my voice carries over my laptop mic.

I am trying to get my usb logitech headphones to work...since I have three pairs...one just arrived with my new space navigator. 

My question is if you were able to achieve voice thru headphones and if so what steps did you take to do so? And if so are your headphones and mic mini jack or usb?

I am VERY new to Linux. I am running latest Ubuntu 8.04 on a hp pavillion dv9000 1.6 process with 2 gig ram and the latest versions of both wine and SL client.

Running SL on this laptop with Vista I get 4-5 fps where as with Ubuntu I get 19-24fps, so my reasons for working this out are obvious.

Thank you so much!
Cheewha Palen

---

### Post by sizzam on 2008-06-02
> **Dekafox said:**
> *edit* Nevermind, got it working with Pulseaudio

What did you do to get it working with Pulseaudio?

---

### Post by cristiantm on 2008-06-07
It is really NOT polite to tell everybody you found a sollution, but not sharing it...

:(

---

### Post by sizzam on 2008-06-08
Ok, I got voice working with Pulse Audio.  Here's the steps I took:

1.  Install pulseaudio-esound-compat:
```
$ sudo apt-get install pulseaudio-esound-compat
```

This will remove 'esound' (if you have that package installed).

2.  Set all your audio settings to use ESD:
System > Preferences > Sound,  I chose ESD for the first three dropdowns.

3.  Move /etc/asound.conf out of the way if it exists.  If it doesn't exist, skip this step.
```
$ sudo mv /etc/asound.conf /etc/asound.conf.1
```

4.  In your Second Life directory, rename the file SLVoice to SLVoice.bin:
```
$ cd <secondlifedir>
$ mv SLVoice SLVoice.bin
```

5.  Per Ron Overdrive's post [here](https://jira.secondlife.com/browse/VWR-6593?focusedCommentId=60004#action_60004), create a new shell script called SLVoice that references SLVoice.bin:
```
$ cd <secondlifedir>
$ gedit SLVoice
```

Add the following, replace <secondlifedir> with the path to your Second Life installation:
```
#!/bin/sh
if test -x /usr/bin/padsp ; then
   exec /usr/bin/padsp <secondlifedir>/SLVoice.bin "$@"
else
   exec <secondlifedir>/SLVoice.bin "$@"
fi
```

Make this new file executable:
```
$ chmod +x SLVoice
```

6. Set Voice Chat to use OSS in Second Life:
Edit > Preferences > Voice Chat > Device Settings > Choose OSS Software for Output Device (speakers)

Notes:
I seem to have to teleport one time before voice starts correctly.

Also, enabling voice has made Second Life a lot more unstable for me.  My wireless connection tends to die periodically.  If I disable and reenable wireless, everything comes back to life.  Per [this article](http://www.experts-exchange.com/Gamers/MMORPG/Q_23317671.html), I've been lowering my Maximum Bandwidth settings in Second Life to try to correct this.

Feel free to jump in with any corrections if you see any unnecessary steps.

---

### Post by sizzam on 2008-06-13
Just to follow up, I ran into issues with Firefox flash audio if I have my sound settings set to ESD and have Second Life open.

I have been having success getting voice chat to work with all my audio settings set to Pulse and with an **/etc/asound.conf** that looks like this:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

I sometimes have to disable and re-enable voice chat in Second Life to get it to work, or play with the Output settings, changing to 'Alsa on my sound card - digital' back to OSS before it will work.  I'm not sure why disabling/reenabling works.  Eventually I get to the point where I set my Output settings to Alsa Digital and see the entire list of voice chatters populate.  At that point if I switch the Output settings to OSS, I can then hear.

I hope this helps someone...

---

### Post by cayhorstmann on 2008-06-17
When I try this, I get the following message over and over when trying to set the Voice Chat Device settings. 

2008-06-17T21:06:27Z WARNING: ll_apr_warn_status: APR: Connection refused

The microphone doesn't work. (It works fine with Audacity.) 

I can hear sounds in SL, but voice never works for me. (Those squares in the device setup never light up.) 

Do I need to reboot every time I set one of these settings? Or restart X?

---

### Post by Comanchee on 2008-06-17
could anyone on this thread explain to me how to even get secondlife to
open and run on ubuntu. im new to ubuntu and to linux, i downloaded the bz2 files from 2ndlife website, extracted 

moved into the folder and did < ./secondlife  >

here is what i get
__________________________
Warning: Did not register secondlife:// handler with KDE: Directory /home/coma/.kde/share/services does not exist.
./secondlife: line 100: bin/do-not-directly-run-secondlife-bin: No such file or directory
*** Unclean shutdown. ***
./secondlife: line 108: arch: command not found

__________________________________________________

any help would be appreciated

---

### Post by trucker33377 on 2008-07-31
> **Comanchee said:**
> could anyone on this thread explain to me how to even get secondlife to
open and run on ubuntu. im new to ubuntu and to linux, i downloaded the bz2 files from 2ndlife website, extracted 

moved into the folder and did < ./secondlife  >

here is what i get
__________________________
Warning: Did not register secondlife:// handler with KDE: Directory /home/coma/.kde/share/services does not exist.
./secondlife: line 100: bin/do-not-directly-run-secondlife-bin: No such file or directory
*** Unclean shutdown. ***
./secondlife: line 108: arch: command not found



__________________________________________________

any help would be appreciated

to get it to run if your pc can handle it just open the bz2 and open the folder there you will see an icon just before the secondlife logo.. says secondlife simply click that and it should open the secondlife logon screen

---

### Post by honeybear on 2012-01-15
Do you need pulseaudio for : 

 SecondLife-i686-3.2.6.247329 for an USB microphone
? 

obligatory?

Normally, 
you don't need to open any ports for SL to work, it should work with any default configuration.

---

