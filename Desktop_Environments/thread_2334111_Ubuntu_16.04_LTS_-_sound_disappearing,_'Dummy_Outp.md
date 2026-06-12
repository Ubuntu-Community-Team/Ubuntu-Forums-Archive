---
title: "Ubuntu 16.04 LTS - sound disappearing, 'Dummy Output' device appearing"
date: 2016-08-16
forum: Desktop Environments
---

### Post by matti777 on 2016-08-16
Hi, last week I finally updated my 14.04 LTS system to 16.04. Right after the update I noticed this highly annoying issue with audio; it keeps disappearing. When I check the Sound Settings, I notice a output device called 'Dummy Output' has appeared and is selected. If I select my real audio device (and, possibly, stop/resume my audio source) the audio continues to play. This appears to occur at random intervals (anything from 5 minutes to an hour or so).

Exact steps to reproduce (well, on my system..):

[LIST=1]
[*]Starts watching a movie (tried Movies, vlc, SMPlayer)
[*]After a random amount of time the sound disappears, movie keeps playing
[*]Taking a look to Sound Settings.. I notice an incorrect output device called Dummy Output has appeared and is selected  (see screenshot)
[*]I select the correct device and possibly stop/play the video player
[*]Audio resumes properly
[/LIST]

[IMG]http://777-team.org/~matti/tmp/audio_screenshot.png[/IMG]

This is the output for aplay -l:

```

[COLOR=#333333][FONT=&amp]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevices: 1/1[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Subdevice #0: subdevice #0[/FONT][/COLOR]

```


Any ideas appreciated.

- Matti

---

### Post by #&amp;thj^% on 2016-08-16
Well not sure i can help much here but this will help me and maybe others here that can help.
Post back the output of this in the terminal
```
inxi -AG
```
This will show the devices again along with drivers that are installed.
By the way pulseaudio is very buggy on this version...craps out quite a bit for me as well as others.
I usually have good results with:
```
killall pulseaudio && pulseaudio --start
```
and you may have to run those as single commands.

---

### Post by SuperFreak on 2016-08-16
I had problems with my HDMI not working this may help
> **raynys said:**
> I solved in this way:
sudo gedit /etc/pulse/default.pa
commented this line --> load-module module-switch-on-port-available
Saved
Switched my headphone jack from front-panel to back motherboard port and then reboot. Now it works fine.

[https://ubuntuforums.org/newreply.php?do=newreply&p=13476849](https://ubuntuforums.org/newreply.php?do=newreply&p=13476849)

---

