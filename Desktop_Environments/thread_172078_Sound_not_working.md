---
title: "Sound not working"
date: 2006-05-07
forum: Desktop Environments
---

### Post by perky on 2006-05-07
G'day!

Am curious if anyone has had any problems with sound not being audible.  It seems to be muted, as beep/etc plays happily in the background without any error messages). 

I have been experiencing this problem since an update to ALSA earlier this morning.

Anyone else?  Am using Dapper.

Output of: cat /proc/asound/cards
```

0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                     Sound Fusion CS46xx at 0xe8122000/0xe8000000, irq 11

```
Output of: lsmod | grep snd
```

snd_cs46xx             85576  3
gameport               15496  2 snd_cs46xx
snd_rawmidi            25504  1 snd_cs46xx
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         92704  1 snd_cs46xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89736  4 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  13 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_cs46xx,snd_pcm

```
Output of: lspci|grep audio
```

0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

```

Output of: sudo alsactl power 0
```

Power state for card #0 is D0

```

---

### Post by aoupraxay on 2006-05-07
My login sound doesn't work either after today's update.

---

### Post by perky on 2006-05-07
Fixed!

For anyone else having the same problems:

Double click on sound icon,
Edit -> Preferences,
tick 'DAC'

Now you can turn this up (mine was on zero for some reason)

Hope this helps someone!

---

### Post by nojjy on 2006-05-08
[QUOTE=perky]Fixed!

For anyone else having the same problems:

Double click on sound icon,
Edit -> Preferences,
tick 'DAC'

Now you can turn this up (mine was on zero for some reason)

Hope this helps someone![/QUOTE]

No sound here as well on a:
Shuttle SN25P

Double click on what sound icon?

---

### Post by Yaholo on 2006-05-08
what if you don't have 'DAC' in sound preferences?

---

### Post by perky on 2006-05-08
[QUOTE=nojjy]No sound here as well on a:
Shuttle SN25P

Double click on what sound icon?[/QUOTE]

The little spearker icon near your clock.. or type in a termal: gnome-volume-control

---

### Post by perky on 2006-05-08
[QUOTE=Yaholo]what if you don't have 'DAC' in sound preferences?[/QUOTE]

Just try enabling everything and fiddle with levels/toggles...  good luck!

---

### Post by rcarring on 2006-05-08
When I double click the sound icon I am mocked by messages about gstreamer, so I just installed everything I could find with the word gstreamer in it. I have not a sniff of a chance of the nefarious DAC option, because the sound applet insists I don't have a sound card, even though Device Manager has one listed.

What tool do i use in terminal to configure sound?

Or does it happen by magic if the Dapper wizard is in a  good mood at bootup?

---

### Post by bendt on 2006-05-31
I had the same problem after a update from the Dapper repo. I assume it was a kernel update that did this. 

I followed the suggestion above, but I actually had 2 DAC's listed. This didn't work for me. 
I used the Text based alsamixer instead, and by up'ing the volume there for DAC I finally had sound again. I now remember that I had to do something like this a long time ago after a kernel/alsa upgrade.

A tip to anyone with sound problems (I have a CS46xx card in a Thinkpad T21 - for referance):
Start 'alsamixer' in a terminal as root (or sudo). Unmute and turn up one bar at a time. There are quite a few, and try to remember what they were at, but this often works with sound problems.

---

### Post by sinaen on 2006-05-31
WTF is DAC for first

and isnt it very annoying to do this every time the computer startups? i think it is anyway so?
it worked for me to fiddle around with the mixer-settings

---

### Post by PriceChild on 2006-05-31
OK for me... the problem was VIA DXS

---

### Post by CyberBob on 2006-06-02
I had the same problem in kubuntu.  The fix for me was just as perky mentions: typing 

> in a termal: gnome-volume-control

Now I would like to add an applet to my taskbar to control the volume in KDE - anybody know how to do this?  I've been hunting and pecking, but haven't found how to do it yet ...

---

### Post by govedarov on 2006-06-02
When I type this in terminal it says that : I have no GStreamer devices or controls. 
In the preferences when I click on SOUND, I see that in the field default sound card there is nothing. 
Any ideas  ?

---

### Post by Moon Jaguar on 2006-06-04
Man, I had a struggle getting sound at all with all Linux distros I tried (worked on Berry but Berry liked to freeze on me).  I got it to work after checking DAC (it comes up twice on Volume Control's preferences...) and running alsamixer!  Thanks all, I managed to get sound going *finally!!!*... wonder why it is that cat /proc/asound/cards  comes up with this?

0 [V8237          ]: VIA8237 - VIA 8237
                     VIA 8237 with ALC655 at 0xc000, irq 193
1 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                     Sound Fusion CS46xx at 0xeb503000/0xeb400000, irq 201

Alsamixer had it as via8237 as well but it managed...


I've got sound with my speakers but nada with headphones.  Anyone else have their headphones plugged into the soundcard jack and if so, how do you get sound to play through headphones?
:confused:

---

### Post by dreadnought1906 on 2006-06-05
[QUOTE=CyberBob]I had the same problem in kubuntu.  The fix for me was just as perky mentions: typing [/QUOTE]

Running Kubuntu here, and while running **gnome-volume-control** didn't reveal the ever-mysterious 'DAC', running **alsamixer** on the command line showed me that 'wave' was all the way down.  This fixed the problem.

Oddly, each mixer program on my computer seems to show me a different sub-set of the total set mixers available on my sound card.  Never worked out why.

[QUOTE=CyberBob]Now I would like to add an applet to my taskbar to control the volume in KDE - anybody know how to do this?  I've been hunting and pecking, but haven't found how to do it yet ...[/QUOTE]

I think you'll find that **kmix** does the job.

---

### Post by Zap on 2006-06-05
Hey
I've the same problem, the sound play, but there's no sound in fact in the speakers.
So i've checked alsamixer and kmix (as i've Kubuntu) and i can't see DAC...
Where is it please ?
I've tried move and unmute all, but nada](*,) ](*,) 
Thanks for your future help :)

---

### Post by PesVseved on 2006-06-09
I had the same problem on my T21.

What I did was unmuting DAC.

+

After suspend I 

modprobe -r snd-cs46xx
moprobe snd-cs46xx

:-s

---

### Post by ktulu1115 on 2006-06-09
If that doesn't work, try making sure your user is listed in the correct groups in /etc/groups and /etc/gshadow.  I had a major problem with sound before - did a fresh install of Dapper, keeping my /home parition unformatted from a Dapper beta install.  Sound worked fine when a new user was created, however when using the existing user, it wouldn't work.

Try reading another thread - see if it helps any: [http://ubuntuforums.org/showthread.php?t=189929](http://ubuntuforums.org/showthread.php?t=189929)

---

### Post by pkunal on 2006-06-10
OK I was having problems with sound this morning. It was very low.

The problem I have is the Headphone is not working. I brought up alsamixer and gnome-volume-control. I noticed that PCM and Front both control my speakers. 

I guess there is a problem somewhere in alsamixer or my configuration.  I saw posts where people have similar problems. Some are having only the headphones working but not the speakers.

Does anyone have any idea how to fix this. All I can say is PCM and Front need to control different things.

Please reply.

---

