---
title: "Dell M2010 w/ STAC 92XX Ubuntu 7.04 NO SOUND"
date: 2007-10-03
forum: Dell  Ubuntu Support
---

### Post by toddwess on 2007-10-03
I have a Dell M2010 Notebook with the Sigmatel STAC 92XX C-Major HD Audio.

I have installed 6.04 and 7.04 and 7.10 and I have no sound coming out.

In Volume control preferences, it has Sigmatel STAC9221 A1 (OSS Mixer) listed.

In Sound Preferences, Sound Events is set up to have Sound Playback going to STAC92xx Analog.

Still no sound.

Please Help!!!!!

Todd

---

### Post by ImNeat on 2007-10-04
Have you tried using HDA Intel (Alsa mixer) instead? Select it from the drop down section of the volume preferences.

---

### Post by toddwess on 2007-10-04
> **ImNeat said:**
> Have you tried using HDA Intel (Alsa mixer) instead? Select it from the drop down section of the volume preferences.

Yep, tried that . . . no dice.

I went to Alsa and got the latest version of the drivers, but not sure how to install.  I see the "install" command in the folder that I extracted, but not sure how to run it.

Todd

---

### Post by dandanplan on 2007-10-05
Look here: 

[http://ubuntuforums.org/showthread.php?t=501195&page=28](http://ubuntuforums.org/showthread.php?t=501195&page=28)

I did it also that way, but still no sound for me too, maybe you have more luck.

---

### Post by toddwess on 2007-10-06
> **dandanplan said:**
> Look here: 

[http://ubuntuforums.org/showthread.php?t=501195&page=28](http://ubuntuforums.org/showthread.php?t=501195&page=28)

I did it also that way, but still no sound for me too, maybe you have more luck.

Thanks, I'll give that a shot.

I un-installed 7.10 and have installed 6.06 to start from scratch.  While still using 7.10, I downloaded and installed the latest alsa drivers, and it really screwed things up.

Now under 6.06, I have sound out of my headphones, but nothing out of the speakers. 

Is this possibly just a speaker/hardware issue instead of a soundcard/hardware issue?  Perhaps the soundcard can't see the speakers (they are, afterall, mounted in the lid of the notebook)

Any additional thoughts?

Going to try the above solution . . .

Todd

---

### Post by toddwess on 2007-10-10
Okay - I'm running 7.10 again.

I have sound from the headphones, but nothing from speakers.  Alsa loads fine . . . sound card is listed as recognized and active . . . mute and volume buttons work fine, but only get sound when I plug in headphones.

Is there a way to make Ubuntu recognize the internal speakers?

Does ANYONE with the M2010 have sound coming out??

Thanks,
Todd

---

### Post by originalsurfmex on 2007-12-12
i also have the m2010 (awesome computer!) but - i have the same problems, also in gutsy...only headphones, no sound anywhere else.

(i also have a problem with the screen going off during movies, even witih power management turned off from the command line - if u've come across the same thing and solved it, it would be cool if u could pm me)

in the meantime...any guru's out there with sage advice??

---

### Post by tdeboeser on 2007-12-20
Just to bump this up, and keep hope alive.  I've got a M2010 also with no sound from the speakers.  But I do have sound from the headphones.  I've googled for other Linux users with the stac92xx.  

It seems the stac92xx was a problem, but the alsa peps fixed it.  Now I've tried 4 or 5 different methods of workarounds (mostly dl, compiling, different vers of alsa with different options), none of which have fixed our issue.  

I guess, in reference to trouble-shooting the good thing is I was always able to get the same result - no speaker sound - headphones only.   

So my theory - 
    The stac92xx is a "HD,  surround sound" chip, and in the design of the M2010 Dell decided to use "pseudo" surround  speakers.  We have no real sub, left, or right.  We have 4 tiny speakers.  I think Dell got a shim in a driver/firmware that lets the windows driver work without issue.

Just a theory... anyone gotta insider at dell? :)

Tom de

---

### Post by brandoncolorado on 2007-12-31
Hey,

Although I am running an MX3414, it does use the Stac92xx as well.  I have battled this sound problem for over a year.  As of right now, I am listening to a movie!  I got it working today by downloading/installing the latest (1.0.15) stable release of ALSA.  

Is this the version you downloaded and tried?  I am using 7.10.

The installation process was the basic /.configure, make, make install and reboot.

---

### Post by RickMeasham on 2008-01-19
Rather annoyed that no matter what I do, I still can't get sound going on this machine. I paid a fair bit of money for it damnit!

Dell, if you're looking, for the love of God, please talk to the ALSA folks so we can get sound from your machine.

Anyone managed to get bluetooth working?

Cheers!
Rick Measham

EDIT: This post rightly says this is my 'first cup of ububtu' .. ignore any implication that I'm missing something obvious -- I've compiled mercurial several times over the past 18 months and am getting close to the point where I'll start poking ALSA's code in a semi-random matter :-D

---

### Post by rebski on 2008-01-19
[http://www.sigmatel.com/support/](http://www.sigmatel.com/support/)
"SigmaTel does not support end-user products, please contact the manufacturer of your device for customer support, software or driver downloads."

So really, Dell should come through for us.

 I recall seeing that this was listed as a bug waiting to be fixed in Ubuntu but don't have the link to hand.

I, too, shall keep trying and report back with any  success.

---

### Post by brandoncolorado on 2008-01-20
What version of ALSA are you sing Rick?

---

### Post by d@ng3russ on 2008-01-21
This worked for me on 7.10 with the same sound card.  Not sure about 7.04.  

You probably have the SigmaTel STAC9205 HD Audio / Intel-HDA.

There are a couple different ways to get this working. This is the one that worked best for me and should get the sound running for any Latitude D830 or D630 in Ubuntu Gutsy 7.10:

1. Install the linux-backports-modules-generic package. In terminal:

QUOTE:
sudo aptitude install linux-backports-modules-generic



2. Edit your alsa-base file to fix the volume automatically increasing:

QUOTE:
sudo gedit /etc/modprobe.d/alsa-base



At the end of the file that opens up, paste in this line:

QUOTE:
options snd-hda-intel model=dell-m42



3. Save and reboot.

You should here the congos playing once the login screen shows up. The sound is a little wonky for volume adjustment but perfectly usable. Now, if I could just figure out how to turn off the congos...

---

