---
title: "teamspeak with ET ?"
date: 2005-07-14
forum: Gaming &amp; Leisure
---

### Post by ubuntu_demon on 2005-07-14
Hi,

no one in our clan with onboard audio is able to get Team Speak working with ET. If someone got this working please write a howto!. Anyway let's post all things everybody discovers in this thread!

here's info on our clan :
[http://ubuntuforums.org/showthread.php?p=252141](http://ubuntuforums.org/showthread.php?p=252141)
[www.katanoon.nl/ubu-e](www.katanoon.nl/ubu-e)

Our progress so far is :
-do the sound guide from the ubuntuguide : [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)
-sudo apt-get install alsa-oss
-go to the alsa panel from volume control and put your mic volume high and make sure it's not muted
-if necessary go to the switches tab and give your mic a boost
-start teamspeak
-startup et with aoss et (no sound but it starts) :
aoss et (in the ET dir)

this gets the same effect as aoss :
etsound.sh :
 
```

#!/bin/sh
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm1c/oss

```
$sudo ./etsound.sh

Another approach might be to use two devices. For example my volume control says that I have an alsa device and an oss device.

in the /dev/ dir :
ls -al | grep dsp
```

crw-rw----   1 root audio    14,  12 2005-07-14 11:04 adsp
crw-rw----   1 root audio    14,   3 2005-07-14 11:04 dsp

```

Here are some howto's we found ;
[http://forum.goteamspeak.com/showthread.php?t=3530](http://forum.goteamspeak.com/showthread.php?t=3530)
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)
[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=34](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=34)
[http://forums.suselinuxsupport.de/lofiversion/index.php/t15638.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t15638.html)
[http://alsa.opensrc.org/index.php?page=DmixPlugin](http://alsa.opensrc.org/index.php?page=DmixPlugin)
[http://alsa.opensrc.org/index.php?page=OssEmulation](http://alsa.opensrc.org/index.php?page=OssEmulation)

---

### Post by skirkpatrick on 2005-07-14
I found that on the Capture tab of Volume Control, I had to mute my microphone and run my Capture sliders all the way up.  It works for me though people tell me I sound like I'm in a tin can.  Also, I can't use voice activation as sounds from other users get retransmitted.  Even though I can remap my buttons on my MX-500 mouse , TS seems to ignore the mapping and thinks I have only 3 buttons so I have to use an awkward keyboard key for speech.

Now I've also killed Sound Server and I'm not sure what all I ended up doing to get to this point.  I'm not necessarily happy with it.

Oh, I've also got the etsound script running at boot so I don't have to remember to do it whenever I want, especially since you have to run it as su or sudo.

---

### Post by ubuntu_demon on 2005-07-14
[QUOTE=skirkpatrick]I found that on the Capture tab of Volume Control, I had to mute my microphone and run my Capture sliders all the way up.  It works for me though people tell me I sound like I'm in a tin can.  Also, I can't use voice activation as sounds from other users get retransmitted.  Even though I can remap my buttons on my MX-500 mouse , TS seems to ignore the mapping and thinks I have only 3 buttons so I have to use an awkward keyboard key for speech.

Now I've also killed Sound Server and I'm not sure what all I ended up doing to get to this point.  I'm not necessarily happy with it.

Oh, I've also got the etsound script running at boot so I don't have to remember to do it whenever I want, especially since you have to run it as su or sudo.[/QUOTE]
 thnx for the reply

1) you use alsa ?
2) in volume control : which device ? which capture slider ? can you be a bit more specific ?
3) what does your etsound script look like ?

---

### Post by skirkpatrick on 2005-07-14
[QUOTE=ubuntu_demon]thnx for the reply

1) you use alsa ?
2) in volume control : which device ? which capture slider ? can you be a bit more specific ?
3) what does your etsound script look like ?[/QUOTE]

1) Yeah, in *System->Preferences->Multimedia Systems Selector*, Alsa is set for both input and output.

2) In Volume Control - Alsa Mixer, on the Capture tab.

3) I created a script in /etc/init.d called GameSound with executable permissions and changed the owner to root.  It contains:
> 
#!/bin/bash
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

I created a symlink called *S99GameSound* in */etc/rc2.d* with the command:
> 
sudo ln -s S99GameSound /etc/init.d/GameSound

This causes GameSound to be executed on startup by the root user, eliminating the problem with needing su or sudo access to run it.

---

### Post by endy on 2005-07-14
I have a SB Audigy2 and it works perfectly for me. All I did was the usual:

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
``` 

Set my mic to record on 'full volume', with boost, and muted the mic playback volume. This also worked fine on my other system with a SB Live! Value, and even using its onboard soundchip which I think is a VIA chip.

I didn't have to change anything else, hope this helps.

---

### Post by ubuntu_demon on 2005-07-14
[QUOTE=endy]I have a SB Audigy2 and it works perfectly for me. All I did was the usual:

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
``` 

Set my mic to record on 'full volume', with boost, and muted the mic playback volume. This also worked fine on my other system with a SB Live! Value, and even using its onboard soundchip which I think is a VIA chip.

I didn't have to change anything else, hope this helps.[/QUOTE]
 I tried this but I get a black screen when I startup ET

I've got a asus P4P 800 deluxe
this the relevant lspci line :

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC '97 Audio Controller (rev 02)

---

### Post by TristanMike on 2005-08-13
I've got teamspeak running on Ubuntu and I never had to do any of that stuff. I just installed it, and a bit of tweaking of my sound levels from my volume control and off to the races I went.

---

### Post by Youdaman on 2005-08-31
[QUOTE=TristanMike]I've got teamspeak running on Ubuntu and I never had to do any of that stuff. I just installed it, and a bit of tweaking of my sound levels from my volume control and off to the races I went.[/QUOTE]

Your sig at the time I'm writing this post is:

> Common sense is assumptions ugly cousin.
Running ASUS A7N8X Deluxe/Athelon 2200+XP/1GB RAM(dual channel)
GeForce FX 5200(128 MB)/SoundBlaster Live! 

You have a SoundBlaster Live -- that's probably why it works for you without needing to do anything extra. I recall reading something about that card being able to do hardware mixing, and thus it doesn't require installing/configuring any software mixing as described above.

---

### Post by evilghost on 2005-08-31
See [http://ubuntuforums.org/showthread.php?t=60595](http://ubuntuforums.org/showthread.php?t=60595)

Basically, TS is going to lock /dev/dsp and if your card doesn't support hardware mixing you're screwed.

It's a TS issue for not using ALSA/OSS.

---

### Post by h0me5k1n on 2005-09-11
[QUOTE=evilghost]Basically, TS is going to lock /dev/dsp and if your card doesn't support hardware mixing you're screwed.[/QUOTE]
Surely you can use a software mixer to share the device - albeit with a hit on the quality.

Would [THIS](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=asound.conf) work??????

---

### Post by evilghost on 2005-09-11
[QUOTE=h0me5k1n]Surely you can use a software mixer to share the device - albeit with a hit on the quality.

Would [THIS](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=asound.conf) work??????[/QUOTE]

I had already tried that along with DMIX, none worked.

---

### Post by Russ[] on 2005-09-12
sudo echo "et.x86 0 0 direct">/proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: Permission denied

sudo echo "et.x86 0 0 disable">/proc/asound/card0/pcm0c/oss
bash: /proc/asound/card0/pcm0c/oss: Permission denied

any idea's what to do about this?

---

### Post by endy on 2005-09-12
Try ```
sudo su
``` first then type the following: ```

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```Then exit.

---

