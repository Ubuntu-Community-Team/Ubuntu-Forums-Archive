---
title: "Teamspeak + aoss in 8.04"
date: 2008-04-25
forum: Gaming &amp; Leisure
---

### Post by Seraed on 2008-04-25
Good new for those who use Teamspeak and wish to game.

I have been anticipating the 8.04 release for quite some time as Hardy comes with Pulse Audio (PA) installed as the default sound daemon. With PA one should be able to trick any oss apps into thinking they are hogging the sound device, allowing them to play friendly with other apps who wish to use the sound card as well.

Unfortunately my adventures with PA under 7.10 where fruitless and I was stuck with Teamspeak hogging the device no matter what, even using aoss. When I heard that Hardy would use PA, I was ecstatic.

After a fresh install of 8.04 on a spare machine I tried to play a YouTube video and run Teamspeak. No such luck. So I fired up Synaptic and installed the alsa-oss wrapper (aoss) and used it to run Teamspeak. The result: Teamspeak ran, with sound, as well as Amarok, YouTube, and various games that had previously not played well with Teamspeak (mostly games under Wine using Alsa).

If you are having Teamspeak problems and are not on 8.04, I highly suggest the switch.

---

### Post by Psylocke on 2008-04-26
I prefer to run teamspeak under wine... Sound with teamspeak and aoss is not that well, when running teamspeak with wine, sound is much better and it's using alsa as well :)

---

### Post by mriedel on 2008-04-26
aoss teamspeak is pretty unusalbe because the sound quality sucks so hard. Why use the ALSA wrapper when using PulseAudio anyway? Unfortunately, using padsp teamspeak makes my microphone not work in teamspeak (it does anywhere else though). Will try wine teamspeak.

**Update:**
Wine didn't help either. There was an error during the codec intallation but I don't think it really mattered. Still I end up having the same problem (microphone not working) which isn't a big surprise because I use the padsp wrapper for wine as well.

---

### Post by Seraed on 2008-04-26
> **Psylocke said:**
> I prefer to run teamspeak under wine... Sound with teamspeak and aoss is not that well, when running teamspeak with wine, sound is much better and it's using alsa as well :)

Hmm, that is something I never tried. I didn't even think about it because I was using the native client. I should try it on my Gutsy box and see how it turns out.

---

### Post by Seraed on 2008-04-26
> **mriedel said:**
> aoss teamspeak is pretty unusalbe because the sound quality sucks so hard. Why use the ALSA wrapper when using PulseAudio anyway? Unfortunately, using padsp teamspeak makes my microphone not work in teamspeak (it does anywhere else though). Will try wine teamspeak.

**Update:**
Wine didn't help either. There was an error during the codec intallation but I don't think it really mattered. Still I end up having the same problem (microphone not working) which isn't a big surprise because I use the padsp wrapper for wine as well.

I was unaware of padsp until just now :P

---

### Post by Psylocke on 2008-04-26
> **mriedel said:**
> aoss teamspeak is pretty unusalbe because the sound quality sucks so hard. Why use the ALSA wrapper when using PulseAudio anyway? Unfortunately, using padsp teamspeak makes my microphone not work in teamspeak (it does anywhere else though). Will try wine teamspeak.

**Update:**
Wine didn't help either. There was an error during the codec intallation but I don't think it really mattered. Still I end up having the same problem (microphone not working) which isn't a big surprise because I use the padsp wrapper for wine as well.

I tried to use padsp, but my microphone is not working either.

When I install teamspeak using wine, I got some codec errors, but that doesn't seem to matter :)

---

### Post by mriedel on 2008-04-26
Does teamspeak work properly under wine for you? If so, what's your wine sound settings in order to make it work with pulse audio? do you use esound?

---

### Post by Psylocke on 2008-04-27
> **mriedel said:**
> Does teamspeak work properly under wine for you? If so, what's your wine sound settings in order to make it work with pulse audio? do you use esound?

I use a default hardy installation, and used wine-doors which makes some default wine settings at installation.

[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/) (although I don't use wine-doors foor program installations because it's a bit buggy for me, but it does some handy wine configuration.)

I didn't have to change anything on wine to make teamspeak work, just default alsa.

I attached the output of winecfg. only thing what is enabled is alsa.

With this settings, teamspeak is working great.

---

### Post by mriedel on 2008-04-27
Thanks a lot. Can other audio programs (music player etc) properly play sound while you're running teamspeak (or other apps) through wine?

---

### Post by Psylocke on 2008-04-27
> **mriedel said:**
> Thanks a lot. Can other audio programs (music player etc) properly play sound while you're running teamspeak (or other apps) through wine?

I run it together with world of warcraft, so yes :)

---

### Post by mriedel on 2008-04-27
If I set wine's audio driver to ALSA, I get no wine sound at all and the inbuilt sound test fails if any other application that has sound is running - which is no surprise because ALSA's trying to grab the sound device while pulse audio already has it.

**Update:**
I seem to have fixed my mic problem ony by configuring ALSA->Pulse->ALSA as described on [http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_the_ALSA_PulseAudio_plugin](http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_the_ALSA_PulseAudio_plugin). On ubuntu/hardy you can simply run "asoundconf set-pulseaudio" though.

I now run (linux-native) teamspeak through "padsp teamspeak".

**Update2:**
Apparently the quality of the sound input teamspeak is getting just sucks. My microphone works fine in other apps, so it must be due to either teamspeak or pa(dsp).

---

### Post by fatalGlory on 2008-04-27
I can confirm that issue.  I have been trying to play WarCraft III in wine with TeamSpeak.  I'm down to running "teamspeak" and causing teamspeak to grab the sound device and not let wine/warcraft output sound -OR- running "padsp teamspeak" and getting sound output fine in both teamspeak and warcraft (game sound is fine, and I can hear the other teamspeak users fine) but when I talk into my mic, they hear garbled noise.

The mic works fine when not using padsp so that possibility is out.  My guess is that running through padsp (which I gather is a sound device emulator) is just too slow to process the mic input properly.

---

### Post by DasCrushinator on 2008-04-29
So does anyone know how to accomplish this on Gutsy?  I want to be able to play Counter Strike via wine and hear/talk on Teamspeak (and possibly play music as well).

---

### Post by Luister on 2008-05-02
I use TS with Enemy Territory, and found a simple way to make them work together (finally after a long time of testing) and as you can see it was really simple.

1.- Install Linux TS Client
2.- Enable mic boost and test it to work under TS, it should be no problem, still device under TS should be "OSS /dev/dsp"
3.- Force TS to use alsa

[IMG]http://www.cof-clan.net/members/alsa-sound.png[/IMG]

4.- Force ET to use playback only device (/dev/adsp in my case)
Command line parameter to start ET:
```
~/bin/et +set snddevice /dev/adsp
```

And that's it.


An alternative to xfire is gfire for pidgin, which has released ver. 0.7.0

[IMG]http://www.cof-clan.net/members/gfire.png[/IMG]

as for a game server browser try XQF

[IMG]http://www.cof-clan.net/members/xqf.png[/IMG]

---

### Post by DasCrushinator on 2008-05-03
> **Luister said:**
> I use TS with Enemy Territory, and found a simple way to make them work together (finally after a long time of testing) and as you can see it was really simple.

1.- Install Linux TS Client
2.- Enable mic boost and test it to work under TS, it should be no problem, still device under TS should be "OSS /dev/dsp"
3.- Force TS to use alsa

[IMG]http://www.cof-clan.net/members/alsa-sound.png[/IMG]

4.- Force ET to use playback only device (/dev/adsp in my case)
Command line parameter to start ET:
```
~/bin/et +set snddevice /dev/adsp
```

And that's it.


An alternative to xfire is gfire for pidgin, which has released ver. 0.7.0

[IMG]http://www.cof-clan.net/members/gfire.png[/IMG]

as for a game server browser try XQF

[IMG]http://www.cof-clan.net/members/xqf.png[/IMG]

This not only got all the games I was trying to make work with TS to work, but also fixed this (hard to explain) problem I had with TS.

Now my games have garbled graphics.

I can't win.

Someone hold me.

:(

---

### Post by timppa_m on 2008-05-03
For those, who have bad sound quality in **TeamSpeak** (crackling etc.) when using **aoss**, this might work, at least it worked for me :)

-Edit your ~/.asoundrc
> gksudo gedit ~/.asoundrc # For Ubuntu
kdesu kate ~/.asoundrc # For Kubuntu  
(you might want to make backup, if you have already done some tweaking :) )

Paste this inside ~/.asoundrc:
> pcm.snd_card {
     type hw
     card 0
     device 0
}

pcm.output {
     type dmix
     ipc_key 1024
     ipc_perm 0660 # Sound for everybody in your group!
     slave.pcm "snd_card"

     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 8192
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.input {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

## Possible artsd full duplex fix:
#     slave {
#          period_time 0
#          period_size 1024
#          buffer_size 8192
#     }

     bindings {
          0 0
          1 1
     }
}

pcm.dsp0 {
     type plug
     playback.pcm "output"
     capture.pcm "input"
}

ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

pcm.duplex {
     type asym
     playback.pcm "output"
     capture.pcm "input"
}

pcm.!default {
     type plug
     slave.pcm "duplex"
}

And save. After that you can try if crackling has disappered or not. This was the solution in my case. I can now play Flash-videos, listen to music and be in TeamSpeak and everything works. I hope that this helps others too.

Notice that you need to have at least ALSA version 1.0.1 because since that version asym-plugin has been included with ALSA. Also notice that this config might not work directly with your sound card: you might need to change some parameters in output-section to get the best quality of sound. Also this might not work if you have pulseaudio installed(i removed it because my friends didn't like quality of sound when using padsp and TeamSpeak ;) ), i'm not sure, but it's possible.

And for Luister: Notice that there might not be that playback-device on all sound cards. I have two computers and in older one there is /dev/adsp device (and before buying this new laptop i used same tactic as you are :) ), but in my new laptop there isn't. The solution was to use aoss and this config. And for Enemy Territory i recommend this hack: [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/) With this Enemy Territory can play sound through ALSA. It helps a lot :)

EDIT: > **Luister said:**
> 
3.- Force TS to use alsa

[IMG]http://www.cof-clan.net/members/alsa-sound.png[/IMG]

With this you don't force TeamSpeak to use alsa, because TeamSpeak 2 uses only OSS, however with wrapper like aoss you can make it work "almost" like native ALSA-application. You only make ALSA as default sound server and programs use it if they know how :) Apparently Teamspeak doesn't but i'm looking forward to TeamSpeak 3 which should support ALSA natively.

EDIT2: And please forgive me if i have spelled something wrong. English isn't my native language :)

---

### Post by Matyy on 2008-05-05
Oh i really don't get it ^^

aoss teamspeak -> I can perfectly hear, but no microphone
padsp teamspeak -> kills pulseaudio
wine set to alsa -> behaves as if it were oss, (only works when it is the only audio program running)
```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
err:wave:wodOpen Error open: Device or resource busy
```

wine set to oss 
- with aoss: TDSoundOut. Open(DirectSoundCreate): No sound driver is available
- with padsp: kills pulseaudio

wine set to:
- sound is completely distorted, just here some noise, and at the end of each sound, it sounds like darth vader breathing, mic doesn't work.

I am still trying, but it's kinda confusing. with padsp it worked once, when 8.04 wasn't released yet. Wine worked too for a time, but also not really stable, i didn't change the configuration yet it stopped working, but that also was while 8.04 was still in developement.

---

### Post by netjunk1e on 2008-06-28
Ive tried the .asoundrc config file but Teamspeak does not detect a card.

My sound card it s intel ich6.
I have alsa-oss installed
everything is set to alsa in my sound config.

Anything i can do to have audio with teamspeak and firefox or other applications?

---

### Post by mriedel on 2008-07-08
*padsp wine TeamSpeak.exe* has been working for quite a while now for me. I run teamspeak from a (true, non-wine) win xp partition.

---

### Post by peruvianfreak250 on 2008-09-13
> **timppa_m said:**
> For those, who have bad sound quality in **TeamSpeak** (crackling etc.) when using **aoss**, this might work, at least it worked for me :)

-Edit your ~/.asoundrc

(you might want to make backup, if you have already done some tweaking :) )

Paste this inside ~/.asoundrc:


And save. After that you can try if crackling has disappered or not. This was the solution in my case. I can now play Flash-videos, listen to music and be in TeamSpeak and everything works. I hope that this helps others too.

Notice that you need to have at least ALSA version 1.0.1 because since that version asym-plugin has been included with ALSA. Also notice that this config might not work directly with your sound card: you might need to change some parameters in output-section to get the best quality of sound. Also this might not work if you have pulseaudio installed(i removed it because my friends didn't like quality of sound when using padsp and TeamSpeak ;) ), i'm not sure, but it's possible.

And for Luister: Notice that there might not be that playback-device on all sound cards. I have two computers and in older one there is /dev/adsp device (and before buying this new laptop i used same tactic as you are :) ), but in my new laptop there isn't. The solution was to use aoss and this config. And for Enemy Territory i recommend this hack: [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/) With this Enemy Territory can play sound through ALSA. It helps a lot :)

EDIT: 
With this you don't force TeamSpeak to use alsa, because TeamSpeak 2 uses only OSS, however with wrapper like aoss you can make it work "almost" like native ALSA-application. You only make ALSA as default sound server and programs use it if they know how :) Apparently Teamspeak doesn't but i'm looking forward to TeamSpeak 3 which should support ALSA natively.

EDIT2: And please forgive me if i have spelled something wrong. English isn't my native language :)

this worked perfectly for me
but i made my sound driver /dev/audio
and of course ran TS as aoss.

---

