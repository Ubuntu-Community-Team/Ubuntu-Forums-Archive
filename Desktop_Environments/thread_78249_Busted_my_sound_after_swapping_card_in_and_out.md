---
title: "Busted my sound after swapping card in and out"
date: 2005-10-18
forum: Desktop Environments
---

### Post by greyhound4334 on 2005-10-18
Arrgghhhh! I hate Linux sound.

I've got on-board sound on my Asus A8NE (sorry, I forget the sound chip, but it used the intel8x0 driver). It was working OK, with the usual complaints about artsd, amarok and mixing sounds with other apps (lately, the desire has been to use soft-phones for VoIP).

Finally decided to try throwing my SoundBlaster Live card in the machine. Couldn't get any sound from either sound device.

So I removed the SB card, thinking that I'd at least get my semi-working, frustrating, crappy, but-at-least-I-can-listen-to-my-music sound back.

Now it's all broke.

Rebooted the machine, and there's no trace of the emu101k (or whatever it was) drivers associated with the SB. The onboard drivers look normal, though I'm not sure how to verify. But here's output from lsmod:

```
lsmod | grep intel8x0
snd_intel8x0           20416  6
snd_ac97_codec         52488  1 snd_intel8x0
snd_pcm                51080  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    28260  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc          6216  2 snd_intel8x0,snd_pcm

```

So how do I know it doesn't work? No KDE desktop sounds. No test sound plays in the KDE Sound System Control module. Amarok doesn't play anything.

God, I hope I don't have to spend 2 days digging around alsa, artsd, and sound driver (non)documentation to get this thing working again! Any gurus out there that can help track down how I busted it and how to get it back again?

Thanks,
john

---

### Post by Cathbard on 2005-10-18
Two things I can suggest.

I use a Soundblaster Audigy 2. I disable the onboard sound and only use the Audigy. To do this I have this in /etc/modprobe.d/sound

options snd-emu10k1 enable=1 index=0
options snd-intel8x0 enable=0 index=0
alias snd-card-0 snd-emu10k1
alias snd-intel8x0m off

If you still have your soundcard removed (The soundblaster Live series *can* be a pain) you may want this in yours:

options snd-intel8x0 enable=1 index=0
alias snd-card-0 snd-intel8x0m 

The other thing sounds really obvious but have you checked the "enable the sound system" box in the sound system part of the kde control panel?

---

### Post by CAE on 2005-10-18
[QUOTE=Cathbard]The soundblaster Live series *can* be a pain[/QUOTE]

It's anecdotal, but I beg to differ. I've found, for the most part, the Live series works pretty well with Linux and I've had no problems using mine with Fedora, a few problems with Ubuntu and none with Kubuntu.

Anyway, [here's my HOWTO](http://ubuntuforums.org/showthread.php?t=76978) on configuring multiple soundcards to work with Kubuntu. In it, I don't mention what my cards are, but the PCI is a Soundblaster Live and the onboard is whatever is on the ASUS A7V333 motherboard, so I don't think it should be too different for the OP.

---

### Post by bluck on 2005-10-18
I too, have had great success with the sb live.  its the one i go to when the onboard lets me down :)

---

### Post by Cathbard on 2005-10-18
I'm glad to hear it. They used to be a problem. That's one thing I lke about open source..........busted today, fixed tomorrow.

---

### Post by greyhound4334 on 2005-10-18
Thanks for the replies.  Very interesting!

So, first thing is I've got no /etc/modprobe.d/sound file. I've got a HUGE /etc/modprobe.d/alsa-base file though, and it's got a WHOLE LOTTA stuff in it.  I don't really know anything about how the modprobe.d stuff works (off to try to read about that), but this at least interesting, if not the cause of my problem.

Anyway, I wanted to play around with the options you suggested for the sound file (trying enabling one or the other card), but I'm a little stuck at this first step  :( so any ideas appreciated.

I'd like to get two sound cards working, so I've printed off CAE's HOWTO (though I note that you seem to desire running ONLY the SB card, not the onboard, and so this HOWTO may not be quite right for me).

Thanks again for the input.
john

edit: Oh, by the way, yes, I've enabled sound in the KDE sound system control module.  And I've also verified that my channels aren't muted.

---

