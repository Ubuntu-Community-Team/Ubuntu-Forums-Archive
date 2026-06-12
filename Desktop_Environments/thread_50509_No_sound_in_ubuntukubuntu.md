---
title: "No sound in ubuntu/kubuntu"
date: 2005-07-20
forum: Desktop Environments
---

### Post by linuxeiro on 2005-07-20
Hello. I have a Realtek AC'97 soundcard integrated in my PC's motherboard. It is not recognised by ubuntu/kubuntu and I can get no sound. How can I configure Kubuntu/ubunto so that it emulates a default sound blaster card? is there someway so that I can get any sound from my soundcard? Thank you

---

### Post by varunus on 2005-07-20
Can you post the output of "lsmod | grep snd" in a terminal?

---

### Post by linuxeiro on 2005-07-20
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

---

### Post by varunus on 2005-07-20
Looks to me like your sound card is being recognized...Can some applications play sounds?  And not others?  The AC97 cards need a little tweaking to make everything play well with sound.  Follow this howto:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

However, I recommend using the following /etc/asound.conf (since I have your card and this one works great for me, no problems, and full duplex):

```
pcm.card0 {

  type hw

  card 0

  mmap_emulation true

}

pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP output device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

```

Good luck.

---

### Post by linuxeiro on 2005-07-20
Hello, yes theoretically it recognizes the card but still i can get absolutely no sound.. how can i change asound.conf ? should i simply copy and paste your settings for this file,since we both have the same card?

---

### Post by linuxeiro on 2005-07-21
Hello varunus, I've done all you indicate in that post and still sound is not working. Is there any other way to fix it? thanks

---

### Post by vedro on 2005-07-21
ellow....

That I wont open another similar topic I would like to ask about my problem.
I have Kubuntu on R40 Laptop and soundcard is recognised and I have soun, but not allways. The thing is that when I listen to the music/watch a movie after starting the computer there is sound. But later there is no sound. Actually is (if I put alsamixer to maximum) but this could not be called a sound. It sound like somebody is burping  :razz:  I have read on this forum that arts could be blamed for this. So is it arts fault? How can I fix this problem?

have a nice day,
vedro

---

### Post by varunus on 2005-07-21
eiro,

Are you using Ubuntu or Kubuntu when sound doesn't work?  If you're using Kubuntu it could be the arts sound server...try turning off KDE sounds from the control center, then go to a console and type:
```
aplay /usr/share/sounds/login.wav
``` 
Do you hear the login sound and see some information about the playback?  Or does the program simply do nothing (and you have to CTRL-C to close it)?

You may want to try setting ARTS to output to ALSA or ESD in the control center under the sound server section.  (Sorry for vagueness, but its been a while since I've used KDE.  I remember that I did get sound to work on this sound card, though.)

And yes, you should just make a new file for /etc/asound.conf and copy the text I posted into it.  Use gedit or kwrite, or your favorite editor.

vedro,

Sorry, I'm not that familiar with ARTS and sound quality.  I never had burping problems though...I know you can configure it in the KDE control center, maybe try if you can change the output device to ALSA, or ESD.

---

### Post by linuxeiro on 2005-07-22
Hello! finally I have solved the problem by downloading and installing a linux driver provided by realtek, which I downloaded from here:
[http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True#8Unix%20(Linux](http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True#8Unix%20(Linux))

The name of the zip file is linux_r32.zip     It has to be unzipped until you get an alsadriver-1.0.9rc4a  directory. I opened a terminal, then I went to that directory and made a
./configure
make
make install
./snddevice

Previously I had to download gcc, linux-source and linux-headers via synaptic. I post the solution here so it can be seen by any other user who has a realtek ac'97 and is not getting any sound in ubuntu 5.04.  Thank you!

---

### Post by varunus on 2005-07-22
You may want to post step by step instructions over in the Tips and Tricks section of the forum, I know people would appreciate it.  Glad newer ALSA drivers got it working...Breezy will include the newest ALSA, so a lot of problems should be fixed by then.  (A lot of cards don't seem to work with 1.0.8 ALSA...)

---

### Post by skyboy on 2005-07-22
I have the exact same card on my laptop and it's been always working under kubuntu, with ESD, OSS and ALSA.

Strange,
to be able to have multiple sounds from different prog, i just modified : 
$sudo vi /etc/esound/esd.conf
---------
[esd]
auto_spawn=0
default_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
#default_options=
----------
work like a charm.
my lsmod | grep snd
intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm

---

### Post by varunus on 2005-07-22
I also have the same card, and mine worked out of the box in Ubuntu, I had to configure ESD and ALSA dmix to hear multiple sounds from everything though.

I guess it just works with some variants of the card.

---

### Post by linuxeiro on 2005-07-22
Hello. I added a post to the tips and tricks forum, in case somebody had the same problem as I. Some people have told me Realtek AC'97 worked for them from the very  installation of Ubuntu 5.04. I think Hoary may have had some troubles in my case because my AC'97 is integrated in an Asrock k8 upgrade 760GX motherboard. This I say merely as a hint, since I am absolutely no computer expert, but an ordinary desktop user, and I am totally newbbie at Ubuntu (which, by the way, is the and most stable and user-friendly linux distribution that I've tried :) )

---

### Post by vedro on 2005-07-23
ellow

[QUOTE=skyboy]I have the exact same card on my laptop and it's been always working under kubuntu, with ESD, OSS and ALSA.

Strange,
to be able to have multiple sounds from different prog, i just modified : 
$sudo vi /etc/esound/esd.conf
---------
[esd]
auto_spawn=0
default_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
#default_options=
----------
work like a charm.
my lsmod | grep snd
intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm[/QUOTE]

So, you have the same laptop? well when I start artscontrol and look in the Audio manager I have KDE System notifications --> type: play --> bus: out_soundcard
when I type artsshell status:
server status: running, autosuspend disabled
real-time status: not started through real-time wrapper
server buffer time: 92.8798 ms
buffer size multiplier: 1
minimum stream buffer time: 92.8798 ms
auto suspend time: 0 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: full
device: default
fragments: 4
fragment size: 4096

Bu there are no system sound, no nothing!! 
And in this situation in the Arts Master Volume, the scale becames red --> equilizer is showing some "action" but there is no sound. There is only sound when I start/restart my computer. And after some time, there is no sound again. But I have noticed one interresting thing: I have not apmci (apcpi, damn I cannot remember how it was written) installed --> I have disable it when installing the system.. So, I have set-ed up in the BIOS that my screen would turn off after 1 min. And for example when I am listening to the music (as soon as I turn on the PC) and the screen turnes of, the sound "flickers"... Any connection with the soundcard and apcpi support. 
I`m desperate, I do no know what to do. Only this is the problem everything is working like a charm.. And I am sad that I cannot watch a movi, listen to the music whenever I want, but just at start up.  ](*,) 
skyboy, could you please write me all your audio settings that you have (all settings that you can think of), please, it might help 

have a nice day, 
vedro

PS:
my lsmod | grep snd
snd_intel8x0           29984  3
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

esd.conf:
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

---

### Post by skyboy on 2005-07-25
As I posted before, 
we have a little difference in the esf.conf
auto_spawn=0
default_options=-terminate -nobeeps -as 2  // ->here you have 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
#default_options=  // -> I have this commented

otherwise, i dunno what I could give you more. Maybe try to reset your bios default values and the enable pcmcia (if i remember well, the card has some connection with that bus when intergrated onchip)

good luck and ask anything you want

---

### Post by vedro on 2005-07-27
ellow

Well, I was so desperit and didn`t know what else to do. So I did the last thing what you can do, I have "reseted"  BIOS... and now (I quess by good`s will) sound is forking like never god before  :)  Pekuliar but ok

tnx ya all for the help,
vedro

---

