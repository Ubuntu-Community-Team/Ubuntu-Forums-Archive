---
title: "Sound works, sound doesn't work, sound....."
date: 2005-09-27
forum: Desktop Environments
---

### Post by lowey23 on 2005-09-27
Hello, everyone. I am very new to Ubuntu/linux. Using Kde. I have an AMD duron with inbuilt soundcard. Have had sounds working and have even managed to import my songs from my old PC which works on M$, and listen to lots of them. Storm approaching, so turned off machine in case of power failure. On starting, no sound. No system sounds, no nothing. Have looked at the forums and tried the fixes at starter guide but to no avail. I have Alsa but the sound system will not work with that and it would work with OSS but not now. Could someone tell an old man where he may be able to find out what it is he has done stupid. Or should I just wait for Breezy and hope that that works for me.

---

### Post by Paperjam on 2005-09-27
Please try a few things:
Start *kmix*. Does it show you a few sliders?
If yes, your soundchip has probably been detected. Is the output-volume turned up?
Next, run *kcontrol*. Goto *Sounds & Multimedia*, *Sound System*. Check if the *sound system* is enabled.
If it still does not work, run *konsole* and try *sudo cat /proc/asound/cards*. Does it show your sound-card? Also try *sudo cat /proc/asound/modules* to see which modules your card needs. Do *sudo lsmod | grep NameOfTheModule* to see if the module is loaded.

---

### Post by mlomker on 2005-09-27
> Please try a few things:

Wow!  I am ***so*** going to keep this post handy for helping others with sound problems.  These commands are great.

---

### Post by lowey23 on 2005-09-27
Thanks for your prompt reply.

1. Kmix shows sliders and output volume is up.

2.Kcontrol sound system enabled. When I try to set hardware to ALSA I get the following error message
"Informational artsmessage
Sound Server informational message
Error while initializing the sound driver:
device: default can't be opened for capture (Invalid Argument)
The sound server will continue, using the null output device."

3. sudo cat /proc/asound/cards tells me I have a VIA 8237

4. sudo cat /proc/asound/modules tells me snd_via82xx

5. sudo lsmod9etc)gives me
snd_via82xx            25248  1
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7168  1 snd_via82xx
snd                    50276  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
gameport                4608  2 snd_via82xx,analog

I'm not sure what all that means.

Thanking you again.

---

### Post by lowey23 on 2005-09-27
[QUOTE=mlomker]Wow!  I am ***so*** going to keep this post handy for helping others with sound problems.  These commands are great.[/QUOTE]

Thank you, sir, for your reply. I have tried the places you suggested and still no luck. I have had a few things with my ubuntu box which I have already sorted with help from these excellent sites. I am, however, going around in ever decreasing circles with this one and am afraid that I'm about to run up my own..............well, you know. I realise that this has been discussed over and over but everything I have so far tried has failed. That is why my first post on your excellent forum has been on this very boring topic. I apologise, but I didn't know what else to do. Thanks again.

---

### Post by mlomker on 2005-09-27
Try running a program that uses sound using sudo.  **kdesu kaffeine** on the run line and then open an MP3 file.  

Sometimes the user account isn't in the 'audio' group and it's actually a permissions problem.

I'm attaching a screenshot of Kmix just to make sure that your green bulbs are bright like mine (meaning that they are enabled).

---

### Post by lowey23 on 2005-09-27
[QUOTE=mlomker]Try running a program that uses sound using sudo.  **kdesu kaffeine** on the run line and then open an MP3 file.  

Sometimes the user account isn't in the 'audio' group and it's actually a permissions problem.

I'm attaching a screenshot of Kmix just to make sure that your green bulbs are bright like mine (meaning that they are enabled).[/QUOTE]

tried kdesu amarok (never had any luck with kaffeine) and received

amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Error: "/var/tmp/kdecache-garylowe" is owned by uid 1000 instead of uid 0.
QObject::connect: Cannot connect Engine::Base::statusText( const QString& ) to (null)::shortMessage( const QString& )
QObject::connect: Cannot connect Engine::Base::infoMessage( const QString& ) to (null)::longMessage( const QString& )
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Error: "/tmp/kde-garylowe" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-garylowe" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-garylowe" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-garylowe" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-garylowe" is owned by uid 1000 instead of uid 0.
amaroK: [Loader] amaroK is taking a long time to load! Perhaps something has gone wrong?
garylowe@ubuntu:~$ Error: "/var/tmp/kdecache-garylowe" is owned by uid 1000 instead of uid 0.
TagLib: ID3v2.4 no longer supports the frame type TSIZ.  It will be discarded from the tag.
Error: "/var/tmp/kdecache-garylowe" is owned by uid 1000 instead of uid 0.

again, being very new to all this, I don't know what it's telling me.
Thanks

---

### Post by lowey23 on 2005-09-28
Thank you to the kind people who responded to my post. I have now got sound again. I looked (again) at the ubuntu starters guide and re-tried the "getting sound working properly in GNOME" instruction, only this time I tried it in the GNOME window instead of KDE. After restart, I could hear some pops where there should have been sounds, so I tried another restart and away it went, good as gold. It may well pack it in again in the future but I am hoping that the release of Breezy (when available for use) may fix whatever the problem was. Once again, thank you for your time.

Gary

---

### Post by Perkele on 2005-09-28
I apear to have exactly same problem(it gives me same errors)...

When I start my computer there is no sound, and when I start Amarok I get...

"Informational artsmessage
Sound Server informational message
Error while initializing the sound driver:
device: default can't be opened for capture (Invalid Argument)
The sound server will continue, using the null output device."

The problem disapears if I restart my computer and reapears if I completely shut down the computer and then start it up. During shutdown, if the sound didn't work alsa gives an error, something like "incorrect card number". It flashes on the screen for couple of seconds before the shutdown continues...

I have AMD Athlon XP with inbuild soundcard, motherboard is some obscure Compaq's own model. I used to have this same problem on my previus ubuntu installation too, and in Mandrake before it...

Oh, and sorry for bad english.

---

