---
title: "Low recording volume and non-working-mic-plug, Dell XPS M1530 with 8.04."
date: 2008-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JSHN on 2008-06-18
Hi,

I've tried to solve this problem for a long time now but with no success. When I try to record something with the internal mic it's very very low volume, barely so you can hear it, the sound is working like a charm on playback and so on but not the mic. Tried many different programs but the problem is the same in all of them, also I've heard more people with these problem but no one have solved it. I've also tried with an external mic but that plug on the PC doesn't work at all in Ubuntu. =(

I've tried everything for several days, searched internet and alot of forums but nothing helps. Tried to maximize recording volume on all the channels also maximized playback volume, nothing, installed: linux-backports-modules-2.6.22-18-generic (which solved the problem that my WLAN-led was off even when it was activated.=)) but still low mic and no plug. Updateded my system to 2.6.22-19 yesterday but nothing, does anyone have the same problem and solved it, or anyone might know why it's like this?

Else I want to say that this forum is the reason that I'm using linux 100% today and loving it more and more for everyday, thank you! :D

---

### Post by tomplast on 2008-06-18
> **JSHN said:**
> Hi,

I've tried to solve this problem for a long time now but with no success. When I try to record something with the internal mic it's very very low volume, barely so you can hear it, the sound is working like a charm on playback and so on but not the mic. Tried many different programs but the problem is the same in all of them, also I've heard more people with these problem but no one have solved it. I've also tried with an external mic but that plug on the PC doesn't work at all in Ubuntu. =(

I've tried everything for several days, searched internet and alot of forums but nothing helps. Tried to maximize recording volume on all the channels also maximized playback volume, nothing, installed: linux-backports-modules-2.6.22-18-generic (which solved the problem that my WLAN-led was off even when it was activated.=)) but still low mic and no plug. Updateded my system to 2.6.22-19 yesterday but nothing, does anyone have the same problem and solved it, or anyone might know why it's like this?

Else I want to say that this forum is the reason that I'm using linux 100% today and loving it more and more for everyday, thank you! :D

Which version of Ubuntu (or any other distro) are you running? Gutsy? Hardy? Something?

Have you looked through this thread [http://ubuntuforums.org/showthread.php?t=702642](http://ubuntuforums.org/showthread.php?t=702642) ? If not then please do, it seems that some people managed to solve it.

---

### Post by JSHN on 2008-06-18
I'm using Ubuntu Hardy (8.04).
I've already looked through that thread but nothing helped. Also I didn't want to install the alsa-drivers that should be used on 7.10 and if the microphone does NOT work, mine works but just very low volume.

I cannot be the only one with this problem, can I? =/

Thanks for your replay anyway!

---

### Post by hob on 2008-06-18
I have the same problem. I'm not sure about the internal mic working (I can't seem to get it working, but I exclusively use an external mic).

I've got a Dell Insprion 1420n. It came with 7.04 preinstalled. Sound worked fine on 7.04, both playback and recording.

I upgraded to 8.04 fresh install with the standard CDs (when is Dell going to come out with their remastered?....). I'm running the latest kernel 2.6.24-19-generic from the updates.

The output from lspci is 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

When trying to record audio with Audacity, I've tried the different recording sources. OSS from /dev/dsp doesn't record anything, and the two ALSA options (ALSA: HDA Intel: STAC92xx Analog (hw:0,0) and ALSA: default) have an "error while opening sound device." 

I'm trying to get skype to work, I'm running version 2.0.0.68 which (I think) is the latest.

Any help would be great. Thanks!

---

### Post by tomplast on 2008-06-20
I will be able to test it myself in a few days when my XPS M1530 arrives :). Hopefully we will find a solution then.

---

### Post by OffHand on 2008-06-23
I have the same problem. Internal mic works but the recording volume is too low. I was not able to fix it.

---

### Post by JSHN on 2008-06-24
Tomplast, we're hoping for you and your expertise now! =)

Else I must say that I am very very pleased with my M1530,
working like a charm except this minor problem, and I know
it will be solved soon. :)

And tomplast, also the first thing you need to do when installing ubuntu is to add: i8042.nomux=1 to the boot, else the touchpad will not work.

---

### Post by tomplast on 2008-06-25
> **JSHN said:**
> Tomplast, we're hoping for you and your expertise now! =)

Else I must say that I am very very pleased with my M1530,
working like a charm except this minor problem, and I know
it will be solved soon. :)

And tomplast, also the first thing you need to do when installing ubuntu is to add: i8042.nomux=1 to the boot, else the touchpad will not work.

Hehe, I noticed :D. I'm glad I bought a mouse for the M1530 ;). I will give your solution a go, but before that I want to keep on trying and trying until (if) I fail :P.

So only the touchpad and the wireless (disabled wifi cather or whatever it was called in BIOS and after that it worked) has been troubling me. I have only had it for like 2 hours so I haven't been able to test the microphone yet, but soon I hope ;).

EDIT: The wireless fix didn't work :/. And the touchpad is a little slow (and I have adjusted the settings).

---

### Post by tomplast on 2008-06-25
Hmm I do agree that the volume is very low. Thankfully I hear something at least, thanks to [http://ph.ubuntuforums.com/showpost.php?p=4753931&postcount=22](http://ph.ubuntuforums.com/showpost.php?p=4753931&postcount=22) for that :). It's not that I have to shout, just talking a little un-low ;)

EDIT: I take that back, partially. in the recording software which came with Ubuntu 8.04 the volume is acceptable but in aMSN it's way too low!


Double-posting, I know... Anyway, I had a Skype>Cellphone conversation just a few minutes ago, and the person on the other end could hear me loud and clear :).

---

### Post by tomplast on 2008-06-26
Sorry, misstake. Please remove.

---

### Post by JSHN on 2008-06-27
Ok, yeah I tried a different software and the volume was ok but with very much background-noise, like the software just boosted the low record volume.
And with my other computers I can enable record volume and playback volume so that you can here what you're saying in the speakers, but that cannot be done with the Dell. =/

Also I tried to fix the mic using aMSN, maybe there is something wrong with that also.

---

### Post by Stratok on 2008-09-26
lol i had same problem..
here is how to solve it:
right click the little sound icon in the top right corner, select "open volume control",  go to edit and then to preferences and check the "mic boost (+20 db)" option...

there u are that solved it for me

---

### Post by tomplast on 2008-09-30
> **Stratok said:**
> lol i had same problem..
here is how to solve it:
right click the little sound icon in the top right corner, select "open volume control",  go to edit and then to preferences and check the "mic boost (+20 db)" option...

there u are that solved it for me

Mic boost? Really? I have searched for such an option for months, was it through gnome-volume-control or some other tool you found this option?

---

### Post by matyasfalvi on 2008-10-24
Hi!

I have a Dell XPS M1330. And here are the steps what I did to increase the recording volume:

[LIST=1]
[*] right click volume control icon on the top right corner of your destktop
[*] go to open volume control
[*] go to edit/preferences
[*] check Digital
[*] increase/decrease recording volume by clicking on the recording tab and scrolling up/down.
[/LIST]

screenshots attached:

---

### Post by liviococcia on 2008-10-24
Hello Members, i have the exact same problem with my internal Mic, a very low capture volume, it's a Dell Inspiron 1720 laptop, i haven't come across any 'Mic Boost' check box in any of the preferences under the volume settings, all capture sliders are to the max.

It's got to be some sort of driver package issue, has anyone found a definitive answer to the problem?

regards

---

### Post by d2globalinc on 2008-10-27
I am having same issue - just got in 10x Dell XPS M1530's - Putting ubuntu 8.04 on them all - The only issue after we got passed the touchpad issue after first install has been this low volume MIC issue.  NO option in volume properties to enable MIC boost - I've tore it apart, tried modprobe.d/alsa-base options from other forums, etc - Still no luck.

Anyone else know how you can manually increase volume of the microphone from the command line for alsa or pulseaudio?

THANKS!

-D2G

---

### Post by kumar_physics on 2008-11-27
MIC PROBLEM SOLVED :)

I tried  the same method as I did for my bluetooth. I hope you guys have dual boot, go to windows and increase the mic volume to max and login to ubuntu . It works :). Same problem with bluetooth, if you diable in windows , it may not work in ubuntu. I feel this windows is doing something with the hardware.

Note: For dell xps mic volume control can be found in dell webcam center.

---

### Post by jespdj on 2008-11-27
Note: You can mark a thread as SOLVED by clicking Thread Tools / Mark as Solved on the top right of the page.

---

### Post by hackel on 2008-12-12
The problem is NOT solved if it requires installing and booting a proprietary operating system merely to CHANGE THE VOLUME!  This must be a bug or missing functionality from ALSA's snd_hda_intel driver.  It is very frustrating, as the only way I can use the mic is to put my mouth right next to the mic against the screen!  We need to get this upstream to the ALSA developers.

---

### Post by vangop on 2008-12-20
Hi all,
I'm on dell vostro 1700 and have xactly the same problem - low volume on the internal mic, and external mic plug is not working.
I'm so happy about my ubuntu 8.10, so that's my major problem now. 
Any help is appreciated (i don't want to install win to fix it)

---

### Post by MooseMagnet on 2008-12-20
One thing that I did to fix mine, but don't if it will help yours.

Install and open Alsamixergui
Select Edit > Preferences (select tracks to be visible)
Check (enable) all the boxes:
Master
PCM
LFE
IEC958
...
...
...
...
etc.

Then adjust the settings of each of these in the Alsamixergui

You can also adjust the settings in a Terminal by typing:
alsamixer

---

### Post by vangop on 2008-12-21
Hi,
I did the tweeks according to 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
and [http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

I dual booted win XP and put the recording volume to max. But, recording volume is still very low - I'm checking it with gnome-sound-recorder.
After I installed pulse control, I can see in Pulse Audio manager the properties of capture device. And there's a volume control slider, which is like on 20% of max and the number already says 100&. If I try to move it, it always returns back to the initial position.
If I do same for output device, the slider goes and shows values over 100%, and it works for output, as the volume is really increased.
I've already tried all I could with alsamixer, and everything is max volume in there.
I've just updated to  2.6.27-9-generic on my 8.10 ubuntu, but still low volume..

---

### Post by linux_tech on 2008-12-21
In a terminal type:

```
gnome-volume-control
``` 

Under File > Change Device, select "Capture: ALSA PCM on front:0 (AD198x Analog) via DMA (PulseAudio Mixer)" and set the master slider to about 80%

 Select the digital input source options and under the options tab, change digital input source to digital mic 1 . Make sure capture is unmuted.

Then try testing Mic

---

### Post by vangop on 2008-12-21
Hi, I tried those already.
I'm posting the screens of what I already have.
First, volume-control settings for capture. The only thing I notice, is that all muted when I open the window, and even if I unmute, they are still muted on next reopen.. Must be some gui bug. But still recording works, but very quiet.
[[IMG]http://img140.imageshack.us/img140/6856/screenshotvolumecontrolsu2.th.png[/IMG]](http://img140.imageshack.us/my.php?image=screenshotvolumecontrolsu2.png)

Next is my system->preferences->sound settings
[[IMG]http://img510.imageshack.us/img510/5904/screenshotsoundpreferenxq2.th.png[/IMG]](http://img510.imageshack.us/my.php?image=screenshotsoundpreferenxq2.png)
I just notice that if I change capture to from pulse to alsa the recording is more clean, but this doesn't affect the volume a bit.

Next, pulse audio control. Manager with devices:
[[IMG]http://img240.imageshack.us/img240/7799/screenshotpulseaudiomancx3.th.png[/IMG]](http://img240.imageshack.us/my.php?image=screenshotpulseaudiomancx3.png)

If I press properties, the next win is:
[[IMG]http://img68.imageshack.us/img68/4822/screenshotsourcealsainpkd2.th.png[/IMG]](http://img68.imageshack.us/my.php?image=screenshotsourcealsainpkd2.png)

The volume bar here can't be set more than 100%, and this is less than half of the bar. If you drag it further, it drops to 100% anyway. In the properties of playback devices from previous screen I'm able to set the volume >100% and it works.

---

### Post by vangop on 2008-12-23
And here's the screen from 
>alsamixer -Dhw
[[IMG]http://img520.imageshack.us/img520/2062/alsadhwht0.th.png[/IMG]](http://img520.imageshack.us/my.php?image=alsadhwht0.png)

and
>alsamixer
[[IMG]http://img377.imageshack.us/img377/3854/alsamixerpulseen6.th.png[/IMG]](http://img377.imageshack.us/my.php?image=alsamixerpulseen6.png)
AND I got the external plug working. Go to VOlume control->Options->Input source should be Analog. Making it Digital Mic switches recording to internal mic.

Still, I have a very low volume on internal Mic. Hope som1 will help me solve it.

---

### Post by Velophile on 2008-12-23
Hi, I've had a similar problem and found the solution (for me) was to change the plughw PCM.  Have a look at this post:

[http://ubuntuforums.org/showthread.php?t=1017625](http://ubuntuforums.org/showthread.php?t=1017625)

Where I've updated with my investigation and solution

The thing to check is the shell output of 

arecord -v -D plughw:0,0 

This'll give you the chain of PCM's that's being used, the problem with mine was the volume control was missing from the chain.

---

### Post by macabro22 on 2009-02-11
> create a ~/.asoundrc file in your home directory such as this one:
```

    pcm.loudmic {
        type asym
        capture.pcm {
            type softvol
            slave.pcm "hw:0,0"
            control {
                name "Mic Boost"
                card 0
            }
            max_dB 20.0
        }
    }
```

You will get a shiny new "Mic Boost" control in the mixer preferences, and if
you select "loudmic" as your input source in Skype, the sound will be
accordingly amplified.. And check the threads on launchpad for other fun tricks

ALSA and Pulse are buggy buggy... please someone acknowledge that ALSA and
PulseAudio have too many _severe_ bugs :) And please let us know how we can
help the ALSA and Pulse teams to fix all these problems :) Thank you

Got this from: [https://bugzilla.redhat.com/show_bug.cgi?id=474477](https://bugzilla.redhat.com/show_bug.cgi?id=474477)

it works on my dell xpsm1730

---

