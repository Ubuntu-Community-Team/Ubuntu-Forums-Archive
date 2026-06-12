---
title: "another &quot;no sound&quot; - M1330"
date: 2008-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2008-09-01
My M1330 laptop has gone mute.  Just test tones can be heard on headphones, loudest with OSS selected, but not at login or with any app.  All is fine under Vista - just Ubuntu is mute.  I checked muting on the volume control GUI and the LED button strip above the keyboard - nothing indicates muting.  This started after a Dell field tech installed a new CD/DVD drive and a Dell phone rep had me install a new driver for it.  The audio chip is a SigmaTel STAC9228, but the SigmaTel website doesn't have downloads available anymore.  The kernel is 2.6.24.19-generic, and the BIOS is version A12.
1) Where can one get the Linux audio driver for the chip?
2) How does one install it in place of the current driver?
3) What settings should be made in System | Preferences | Sound?

I've done the usual Google and forum searches with no luck.
Any info would be appreciated.

*TimDaniels*

---

### Post by subzero27 on 2008-09-01
Have you tried contacting dell ???? maybe they would have an answer.

---

### Post by TimDaniels on 2008-09-01
> **subzero27 said:**
> Have you tried contacting dell ???? maybe they would have an answer.

My laptop is not am "M1330n", i.e. not pre-installed with Ubuntu.  It's an "M1330", i.e. pre-installed with Vista, so Dell tech support won't help me with Ubuntu problems.  And, yes, I did call Dell, and the tech rep could only point me to Google and these forums.

*TimDaniels*

---

### Post by superm1 on 2008-09-02
There are no "extra" drivers for the IDT audio chips in these machines.  The ALSA included hda-intel driver has support for sigmatel codecs already.

If you are having issues, I would try a few things:

**Clean up the ALSA state file**
1) sudo /etc/init.d/alsa-utils stop
2) Remove /var/lib/alsa/asound.state
3) sudo /etc/init.d/alsa-utils start

**Try booting off an Ubuntu 8.04 disk to rule out any configuration related issues**
Things should come up by default with audio supported on the 1330.

---

### Post by TimDaniels on 2008-09-02
The **sound is back** and the Duck quacks again!  You da Man, SuperM1!

What I did was essentilly your 1st suggestion:
```
[b]sudo /etc/init.d/alsa-utils stop
sudo rm /var/lib/alsa/asound.state
sudo /etc/init.d/alsa-utils start[/b]
```


I also find that the **single slider** that appears by left-clicking the speaker icon **has no effect** except muting when the slider nears the bottom of its range.  To get a slider that controls the sound level, I have to right-click the speaker icon and select "Open Volume Control", and for a slider to work, the Device type in the Volume Conrol panel must be either
"0:  HDA Intel (Alsa mixer)" - for which I must use the "Master" slider with the other 2 sliders all the way up, or
"1:  Sigmatel STAC9228 (OSS Mixer)" - which provides just one slider.
**Is there a way to make the single slider that appears with a left-click on the speaker icon control the sound level?**

*TimDaniels*

---

### Post by superm1 on 2008-09-02
> **TimDaniels said:**
> The **sound is back** and the Duck quacks again!  You da Man, SuperM1!

What I did was essentilly your 1st suggestion:
```
[B]sudo /etc/init.d/alsa-utils stop
sudo rm /var/lib/alsa/asound.state
sudo /etc/init.d/alsa-utils start[/B]
```
I also find that the **single slider** that appears by left-clicking the speaker icon **has no effect** except muting when the slider nears the bottom of its range.  To get a slider that controls the sound level, I have to right-click the speaker icon and select "Open Volume Control", and for a slider to work, the Device type in the Volume Conrol panel must be either
"0:  HDA Intel (Alsa mixer)" - for which I must use the "Master" slider with the other 2 sliders all the way up, or
"1:  Sigmatel STAC9228 (OSS Mixer)" - which provides just one slider.
**Is there a way to make the single slider that appears with a left-click on the speaker icon control the sound level?**

*TimDaniels*
Yeah, just right click it and hit the preferences button.  Pick the mixer you want.

---

### Post by TimDaniels on 2008-09-03
> **TimDaniels:]Is there a way to make the single slider that appears with a left-click on the speaker icon control the sound level? [QUOTE=superm1 said:**
> Yeah, just right click it and hit the preferences button.  Pick the mixer you want.[/quote]

That worked!  I didn't realize that "select a track" meant "select a slider".  I guess I'm not cut out to be an audio engineer.  :-)
Thanks, SuperM1.

*TimDaniels*

---

### Post by zaphodz on 2008-09-19
Thanks for this guys :)

Sound works again on my Dell XPS M1330 :)

Much appreciated.

---

### Post by NuSuey on 2008-11-24
Thank you very much ;) helped today when alsa didnt worked for the sound - only oss .. thanks ;)

---

### Post by SnowflakeRV7 on 2009-01-21
I just tried this on my XPS 1330 (no headphone output, but internal speakers work), and on the 'sudo /etc/init.d/alsa-utils start' line I got a bunch of "Invalid card number" errors from aumix.  Drat.  And still no sound out of the headphones.

---

### Post by SnowflakeRV7 on 2009-02-25
Still no joy with the headphone output on the Dell XPS 1330 running Ubuntu 8.10.  Internal speakers work fine after installing the latest ALSA driver as recommended in other threads.  Headphone output doesn't work at all (on either headphone jack) and when I plug in a pair of headphones the internal speakers don't automagically shut off like i'd expect them to.

Is *anyone* else experiencing this?  I have never had so much trouble with this laptop as I have once switching from 8.04 to 8.10.  The audio and HDMI were completely toasted by the upgrade, forcing a series of hacks to get them going again.  Now running latest nVidia drivers to get HDMI out working, and latest ALSA drivers to get internal speakers working (and audio working over HDMI).

Which is anoying because all of this worked out-of-the-box when I installed 8.04 originally.

Sigh.  The pains of running Linux sometimes make me wonder if it's worth it.  :)

---

### Post by Yumi on 2009-03-03
Also get the "Invalid Card Number" Error. Any advice?

Michael

---

### Post by giorgio.stefanoni on 2009-03-19
I have the very same problem, is there a way to fix this?

Giorgio

---

### Post by linuzo on 2009-04-10
You need to force ubuntu to use the correct audio driver..  

So do sudo nano /etc/modprobe.d/alsa-base

add the following line: options snd-hda-intel model=dell-3stack

Then save and restart alsa. 

I was having really low sound and then when you do this and go to the sound manager in gnome you will see PCM and FRONT to be able to boost the sound. Hope this helps.

---

### Post by kernow on 2009-04-24
I still can't seem to get any sound at all, not from speakers or headphnes, I was running hardy which I fixed the sound for no problems for ages. I've just done a fresh install (not upgrade) and now can't seem to get any sound working at all, and can't find any solutions
I'm running ibex now anyone got any other ideas?

---

### Post by dpolancom on 2009-06-07
I finally could hear sounds but when I make the skype's test call I have to shout to hardly hear my voice. Any suggestions about improving the mic's volume?

---

