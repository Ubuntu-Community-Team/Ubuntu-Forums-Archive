---
title: "Multiple sound cards alsa problem 14.04 Gnome Flashback 3.8.4"
date: 2014-08-14
forum: Desktop Environments
---

### Post by archaeometrist on 2014-08-14
I need help.

I am running a Dell Optiplex 7010 (i7 3.4Ghz, 16Gb ram) with built-in HD IBM sound and AMD/ATI Turks PRO (Radeon HD 7570) graphics.  This is my school/work system, although it is also for home and relaxation use.  (The computer was a major investment because my old system was developing problems that made it unreliable - it was 7 years old and although carefully maintained, started having thermal problems.)

I added a Creative Audigy Fx sound card to it for use with one of my radios (SDR - software defined radio).

The Video card has built-in HDMI audio, which I don't and will probably never use.  Under 12.04 LTS, the audio captured "card 0" under ALSA and Pulseaudio, and nothing could dislodge it - even in essence deleting the card in software meant that there was no card 0 (and ALSA/Pulseaudio started crashing).  I read people who referred to it as the "Audio card from hell" because of problems.  I upgraded to 14.04 to try to fix this problem (it can be dislodged from card 0 now, but still may be a problem).

The Creative board line-in just will not work with my software... I can change settings in the mixer, but no matter what combination or "trick" I try, it only works intermittently (I've spent the last 3 days - morning till after midnight - reading and trying everything I could find in the ALSA documentation and by Googling).  I also cannot make that card =0.  No matter what I try, it usually ends up as card 1 or card 2 (usually card 2).

Part of the problem appears to be the HDMI audio connected with the video card.  There seems to be no way I can turn that off so that it's not recognized by Linux.
Part of the problem is that all three cards use the snd-hda-intel module.  I finally found out that in spite of what I read, vid and pid are not recognized by the snd-hda-intel module.  dmesg reports that they aren't recognized options.

I really need to be able to get this working.  When I'm not working on school stuff (I'm a graduate student), I like to mess around with my radios.  I need this to work in order to have that option (a hobby and break from the grind).
I can't afford to go out and buy a new card (audio or video) - again I am a graduate student (and like most graduate students, dirt poor).

Does anyone know of a way to force the Creative card to be card 0 (all of the usual ALSA tricks don't work)?  Maybe some way of disabling the HDMI audio so it isn't even noticed by Linux?

Finally, is there some way to get a message to the maintainers of snd-hda-intel that adding vid and pid addressing could solve a multitude of woes for a lot of people - and that I'd suggest better (and up-to-date) documentation at ALSA?

Thanks!

---

### Post by archaeometrist on 2014-08-14
I'd like to add - I have another week or so that I can spend trying to get things working, then classes start and I'll be busy.

---

### Post by budgerigar on 2014-08-14
Have you tried adding a file named .asoundrc to your home folder?

You could try reading this for an explanation:
[http://alsa.opensrc.org/Asoundrc](http://alsa.opensrc.org/Asoundrc)

The next option would be to installed alsa-utils, which I think is the package that includes the GUI version of ALSA mixer. I'm not entirely sure if this works when you also have pulseaudio installed.

I always had difficulties with pulseaudio, which is the program that gives a user interface to ALSA. It's not going to be the best idea for many people, but I removed pulseaudio. I then installed jackd, which is a low-latency audio connection program, which can be installed with 'sudo apt-get install qjackctl'. I only guess that this may be an option for you as you mentioned connecting to a radio. For most people wanting to simply connect a sound card, I wouldn't recommend this. If you do go for this option, you will need to log out after removing pulseaudio.

In the JACK audio connection kit's setup, one of the options is "Interface", in which your card should be listed. There can be a lot of messing about with volume levels before it all works. Setting up audio on Linux is very difficult. Ubuntu usually just works straight away with a built-in soundcard, but anything more complicated can be very difficult and time-consuming.

I hope my few suggestions can be of some help.

---

### Post by archaeometrist on 2014-08-16
I tried asoundrc (created some strange problems)... and had been reading reams of info (fighting the problem for over four days straight, morning to after midnight).  Most of what I was working with was at the level of alsa-base.config and udev.  We finally worked it out that it was either a really strange problem with the board's firmware, or very possibly problems with a proprietary driver - and the generic ones weren't any better.  The card is out of the computer now and I'm going to have to wait until I can scratch up enough $$$ to get a better (but hopefully easily affordable) "sound" card that works with both Linux and as part of a multiple card system.

I've kludged together a setup that works, although barely, using an old Creative USB MP3+ sound card.  It's reliable but I've lost sensitivity, dynamic range, and especially bandwidth.

BTW, alsamixer and the gui version both work even when pulseaudio (and also jack) are installed, and even when they're running.  I've got several mixer and control programs installed, and once I get a decent card installed, I'm going to pick the best-working ones and delete the rest.  ALSA.org also has some decent utilities that helped me to figure out why things were not working, such as HDA-Analyzer.  Jack is something I considered as a potential solution, but it's been so long since I'd used it that I'd forgotten how to configure it.

---

