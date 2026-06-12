---
title: "Sound Problem"
date: 2009-01-03
forum: General Help
---

### Post by blurplelove on 2009-01-03
Ever since some updates have been put on my laptop, there has been no sound.

When I click the sound icon at the top it says:
No volume control GStreamer plugins and/or devices found.

I checked and the gstreamers were already installed.
So, yeah. I'm wondering why it's doing that. :confused:
I appreciate the help. :)

---

### Post by blurplelove on 2009-01-03
can ANYBODY help? :/
& thanks in advance!

---

### Post by namdung on 2009-01-03
Ubuntu version? Any specific update? 
Was ur sound fine before the update and were u able to play proprietary formats like mp3 etc? 
Are u able to hear default login sound when Ubuntu first logs in? 
Does ur sound not play at all or it only doesn't play certain proprietary files. 
Are u able to play Youtube videos?

Paste the output of the following
```
less /proc/asound/card0/pcm0p/info
```
```
asoundconf
```

Try removing and reinstalling the GStreamer codecs.

---

### Post by blurplelove on 2009-01-03
yeah ubuntu
and im not sure what updastes were installed.. all i know is that there were 182 of them
yes, the sound wa perfect before the updates
but now i cant here the default login sound, i did before the updates though
i can play youtube videos, but there is no sound at all

acamy@oem:~$ less /proc/asound/card0/pcm0p/info
/proc/asound/card0/pcm0p/info: No such file or directory

acamy@oem:~$ asoundconf
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio


Okay, I'll try doing that. :)

---

### Post by namdung on 2009-01-03
In *System==>Pref==>Sound*, select **ALSA** for all fields on the *Devices* tab and Test to hear for any sound.

Maximize all volume controls using arrrow keys for alsamixer in the terminal.
```
alsamixer

```
Since ur sound was fine before the update, I reckon ur hardware is ok. Do u have any additional sound card which needs a driver? In *System==>Admin==>Hardware Drivers* check if any audio driver is installed and enabled. If additional drivers are required, then it should have been there prior to the updates.

Paste output of 
 ```
aplay -l
```
```
lsb_release -a
```

---

### Post by blurplelove on 2009-01-03
When i tested for sound it gave me this message:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
& there was no sound either. =/

acamy@oem:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
acamy@oem:~$ aplay -l
aplay: device_list:204: no soundcards found...
acamy@oem:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy


& also when i went to system>>> admin
i didnt find the link that said hardware drivers

---

### Post by namdung on 2009-01-03
U r using an old/outdated version of Ubuntu, the latest version being 8.10. Ur Ubuntu is not recognizing the audio drivers now after the updates.

I strongly recommend u install Ubuntu LTS Hardy Heron 8.04.1 which is stable and supported for 3 years. The next release 8.04.2 is out anytime soon with more bug fixed. I suggest try this with a LiveCD and see if everything works, including audio, networking etc and then go for the full install. If ur hardware specs are low, consider Xubuntu.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

I don't think I'll be able to help u further on the older Ubuntu version.

---

### Post by blurplelove on 2009-01-03
Ooohhh, okay. So that's the problem.
Am I supposed to buy the LiveCD?
& how do I find out if my hardware specs are low?
Oh yeah, and thank you. :)

---

### Post by namdung on 2009-01-03
Download Ubuntu for Free if u have enough bandwidth (700 MB). 
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Else Request for a CD or find it in CD/DVD included with some Computer magazines.
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Hardware requirements
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

All version of Ubuntu except the Server and Alternate comes with a LiveCD. This option is available when u first boot with the CD *"Try Ubuntu without any change to your computer"*

Good luck!!!

---

