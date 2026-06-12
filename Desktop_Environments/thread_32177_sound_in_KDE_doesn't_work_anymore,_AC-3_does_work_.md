---
title: "sound in KDE doesn't work anymore, AC-3 does work though"
date: 2005-05-06
forum: Desktop Environments
---

### Post by F for Fragging on 2005-05-06
Ok, something very weird happened. Let's begin with my hardware, I have a Soundblaster Audigy Player soundcard and a Creative Desktop Theatre DTT 2500 Digital 5.1 speakerset. After I installed Kubuntu a month or so ago, all I had to do was unmute the "Audigy Digital/Analog Output Jack" switch in KMix (because in every Linux distro I've ever used it was muted by default, but is done intentionally by ALSA I heard) and then the sound would work. And it has been working ever since I installed Kubuntu, until yesterday.

I was watching a video file with AC-3 sound in Kaffeine. After that I opened another video file without AC-3. But I didn't hear sound anymore. I opened amaroK to check if it was Kaffeine-specific, but amaroK gave me no sound either. I started a game, Enemy Territory, but sound didn't work there either. I rebooted to Windows XP and I noticed that the sound was working fine in Windows XP, so it isn't my hardware. I rebooted to Kubuntu again, but still the sound didn't work, except when I opened a video file with AC-3 again, then I would get sound.

I checked everything in the mixer, but I didn't notice any abnormalities, nothing is muted... very weird, and I have no idea what to do. Can anyone help me with this? If not, can anyone tell me how to "reset" the sound system and it's configuration files, maybe it will return to normal then?

---

### Post by -TayloR- on 2005-05-06
Hmm, this might sound like a stupid suggestion but do you have a webcam connected up? i connected my webcam up and lost all my sound because it defaulted to my webcam being the sound output device, as soon as i disconnected that my sound was back. So have you added anything externally to your computer setup lately? thats all i can really suggest myself, im fairly new to all of this myself :).

---

### Post by F for Fragging on 2005-05-06
[QUOTE=-TayloR-]Hmm, this might sound like a stupid suggestion but do you have a webcam connected up? i connected my webcam up and lost all my sound because it defaulted to my webcam being the sound output device, as soon as i disconnected that my sound was back. So have you added anything externally to your computer setup lately? thats all i can really suggest myself, im fairly new to all of this myself :).[/QUOTE]
 No, I didn't connect a webcam or any other new hardware.

---

### Post by F for Fragging on 2005-05-10
No one can help?

Please guys, help me. I've been without sound for some days now and it sucks, so can anyone please tell me how to reset/reconfigure the KDE sound stuff?

I'm considering to switch to Debian unstable, Kubuntu is so problematic... Konqueror is driving me mad when it crashes when I have ten websites open in tabs, Kaffeine is super buggy. Kubuntu is sooo beta.

---

### Post by ludi on 2005-05-10
Instructions here:
[http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211)
Please, if didn't work out, post it in this thread.
There are many possibles causes for this issue, try to follow the how-to and see what happens...

---

### Post by pHr34kY on 2005-07-01
I'm getting a similar problem with my card. It's an SBLive, but nonetheless lspci tells me it's an EMU10K1:

```
0000:00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
```

What's strange is my card worked perfectly with SPDIF at first. I had XMMS decoding to PCM through the ALSA mixer, and I had totem-xine doing a direct AC3 Passthrough - my amp automatically switched between PCM/DD/DTS as I played different sources.

I broke it when I played PCM through XMMS at the same time I was playing a DTS DVD through totem... I was testing to see what happened when ALSA wanted the sound card while totem had it (since AC3 passthrough takes hardware resources away from ALSA - it bypasses ALSA altogether because it's not decoding). Sure enough.. XMMS crashed, and when I tried it again, XMMS worked but there was no sound. I closed totem and XMMS still wasn't making much noise (although it seemed to open the sound device fine).

...then after a while I figured out:
- PCM was only coming from my card's ANALOGUE output
- AC3 was only coming from my card's SPDIF output

Seriously.. I can play a DVD and an OGG at the same time, and when I switch my amp between SPDIF and analogue I jump between the DVD and the OGG.

I'm assuming that ALSA couldn't open the SPDIF, so it dropped back to analogue.. and for some stupid reason it stayed that way.

What I'm trying to do now is get it back to how it was, and find a way to make it stay that way in the situation where totem-xine and ALSA want the SPDIF at the same time.

Does anyone know how to tell ALSA that SPDIF still exists?

---

### Post by shu on 2005-08-15
I had the same issue. Suddenly SPDIF stopped working in the way that AC3-Pass worked but normal PCM stream didn't. The solution is brutal, but the only one I found as of today. You need to force ALSA not to load settings at boot time. To do it simply:

```
chmod -x /etc/init.d/alsa
```

On the next boot-up alsa will start with 'factory default' so everything will be muted. Just adjust all the gauges you need and once you're set, store the settings:

```
alsactl store
```

After this you can reenable automatic setting loading:

```
chmod +x /etc/init.d/alsa
```

...till it stops working again  :wink:

---

### Post by Osamabingandhi on 2006-06-04
I have the same problem, but couldn't do what you wrote. The error message is: 

chmod: couldn't reach "/etc/init.d/alsa": the file does not exist

i run dapper by the way. Got any idea?

Would be nice to be able to listned to mp3's again :)

---

### Post by homek on 2006-06-19
I have a similar issue. After a thread with DTS have hanged, i do not have PCM through SPDIF. Disabling autoloading of settings did not help (nothing have really changed). How do I recover my SPDIF settings? I would hate to have to reinstall my system.

I use breezy with standard gnome environment.
Cheers
Jan

---

### Post by jogeer on 2006-08-07
This may seem like a silly solution, however, I had a similar problem and this fixed it. 

After several frustrated hours of trying to fix the sound I decided to check the user permissions. The main user didn't have permissions to use audio devices. Upon changing that setting the sound worked again. 

I was almost frustrated that it was such a small thing.

I don't know what changed this. It wasn't me. I will withhold my guesses as to the cause so I don't look totally stupid.

---

### Post by DutchR_PW on 2006-08-15
First, check if the mixer button IEC958 Optical Raw isn't unmuted. If it isn't but you still have no sound, do a sudo alsactl restore.

I hope this helps.

---

### Post by anthonycapo on 2006-09-09
Has anyone found an actual working solution to this issue yet? I'm having this exact same problem now (everything was working fine for months until somehow watching a DVD with AC3 through xine stopped any PCM from going to SPDIF).  I've had the problem once before and the only thing that solved it was a clean reinstall.  My device permissions are fine, no config settings have changed, the mixer is set up exactly as it was before when things were working.  With kernel 2.6.17, I'm not sure how to get ALSA to boot to the factory defaults (there is no init.d entry for alsa), although it doesn't sound like that would help anyway.  

For the time being, I've switched to analog outputs.  BTW, I don't think this is specfic to Ubuntu or KDE - I'm pretty sure it's a kernel/ALSA problem.  However, this is the only thread I can find anywhwere that even addresses this issue, so if anyone has any clues, please help!  I don't wanna reinstall! 
](*,)

---

### Post by zigtah on 2006-09-15
> **shu said:**
> I had the same issue. Suddenly SPDIF stopped working in the way that AC3-Pass worked but normal PCM stream didn't. The solution is brutal, but the only one I found as of today. You need to force ALSA not to load settings at boot time. To do it simply:

```
chmod -x /etc/init.d/alsa
```

On the next boot-up alsa will start with 'factory default' so everything will be muted. Just adjust all the gauges you need and once you're set, store the settings:

```
alsactl store
```

After this you can reenable automatic setting loading:

```
chmod +x /etc/init.d/alsa
```

...till it stops working again  :wink:

Whoah! Thanks man, this totally fixed and/or healed my headache.

And for anthonycapo: the script is located at **/etc/init.d/alsa-utils**, not /etc/init.d/alsa as shu stated above.

Just waiting for the day a permanent solution is found.

---

### Post by Aoestein on 2007-12-03
Well I found a solution that worked for me!
I reinstalled ALSA. And saw that my "IE958 Optical Raw" still was checked, so I unchecked it and WOHA sweet PCM sound.

---

