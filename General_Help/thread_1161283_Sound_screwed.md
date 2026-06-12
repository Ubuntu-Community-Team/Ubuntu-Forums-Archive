---
title: "Sound screwed"
date: 2009-05-16
forum: General Help
---

### Post by Luffer on 2009-05-16
Hi,

I've got myself tied up in knots and I don't know what to do! I had a problem with audio from my line-on not playing through speakers. I also couldn't alter sound levels from the volume control.

I found threads that suggested removing PulseAudio so I followed the instructions. This left me worse off because I couldn't get any sound working.

So then I followed another post showing how to set-up PulseAudio to get things back again. This sort of worked because I've got audio playback, but now I have two volume controls in my panel! Worse still, neither of them can control the audio level!

I daren't do anything else now, I need help! How can I get myself out of this mess and back to square one? I think I need to remove all audio stuff from Ununtu and start fresh, but I've no idea how. Or maybe I don't... I have no clue!

All I know is that I have made a total hash of trying to fix it on my own and nobody to turn to to help :(

Oh, I'm using Jaunty BTW!

---

### Post by Aaardwark on 2009-05-16
If you have the system on a separate partition, I vote reinstall.

Otherwise I would be grateful for a list of the commands you've used in the terminal from start of the mess to the end of it. Everything is solvable.

---

### Post by Luffer on 2009-05-16
Can't really tell you what commands I used because some of it was done it Synaptic etc..

Currently I have a PulseAudio applet and two volume controls in my taskbar (is that what you call it in Ubuntu?).

[IMG]http://farm3.static.flickr.com/2134/3537046752_1c44a6a845_o.jpg[/IMG]

I followed this to remove PulseAudio:

[How to Remove Pulse Audio Ubuntu 8.10 (Intrepid Ibex)]("http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html")

I tried this when re-installing:

[Sound Solutions for Ubuntu 9.04 (Jaunty) Users]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")

I also tried numerous configuration changes in System -> Preferences -> Sound.

Oh, and I also now have two "sound" entries under System -> Preferences!

---

### Post by Aaardwark on 2009-05-16
Well I've read the guides loosely. The sound soulutions guide seems to assume a starting position from a fresh install. Before you do that step you should have restored the system to where it was before the first guide.

Here are some things for the terminal:
sudo apt-get install pulseaudio
sudo apt-get remove esound
sudo mv /etc/X11/Xsession.d/70pulseaudio.back /etc/X11/Xsession.d/70pulseaudio

If you did this step:
cd ~
cp .asound* yourfilename

Reverse it by doing:
cd ~
mv yourfilename .asoundrc

If I don't miss remember I also believe you remove ubuntu-desktop when removing pulseaudio. That could be troublesome when you want to dist-upgrade:
sudo apt-get install ubuntu-desktop


Go to System->Preferences->Startup applications
Check if you've got double sound systems booting.

Tell me how you're doing, and I'll help you from there.

---

### Post by Luffer on 2009-05-16
> **Aaardwark said:**
> 
sudo apt-get install pulseaudio

Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

> **Aaardwark said:**
> 
sudo apt-get remove esound


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package esound is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

> **Aaardwark said:**
> 
sudo mv /etc/X11/Xsession.d/70pulseaudio.back /etc/X11/Xsession.d/70pulseaudio


That worked.

> **Aaardwark said:**
> 
Reverse it by doing:
cd ~
mv yourfilename .asoundrc


mv: cannot stat `yourfilename': No such file or directory

> **Aaardwark said:**
> 
If I don't miss remember I also believe you remove ubuntu-desktop when removing pulseaudio. That could be troublesome when you want to dist-upgrade:
sudo apt-get install ubuntu-desktop


Hmmm, didn't remove that, don't recall being asked to.

> **Aaardwark said:**
> 
Go to System->Preferences->Startup applications
Check if you've got double sound systems booting.

Tell me how you're doing, and I'll help you from there.

In Startup applications I've got "Volume Control" and "PulseAudio Device Chooser".

Still got double icons, sound is working but controls not having any effect. Also can't get anything out of Line-In which was what I was attempting to fix in the first place.

---

### Post by Aaardwark on 2009-05-16
If you didn't remove ubuntu-desktop, you didn't remove pulseaudio. And if you didn't have esound, you didn't install it. Then the file you put back and maybe deselecting or removing the Pulseaudio Manager from System -> Preferences -> Sessions where the only things making your sound not work. 

Pulseaudio would have been reinstalled when installing some of the apps in the configure-guide. Check if you removed ubuntu-desktop. If you removed pulseaudio it would have followed, they didn't specifically tell you to remove it (worst case it will tell you it's already installed): 
sudo apt-get install ubuntu-desktop


If you want to get rid of the extra apps you installed during "sound solutions" (and get the one you lost), I've checked which ones weren't installed on my system:
sudo apt-get remove libgconfmm-2.6-1c2 libglademm-2.4-1c2a libpulse-mainloop-glib0 paman paprefs pavucontrol pavumeter pulseaudio-module-zeroconf xmms2-core alsa-oss asoundconf-gtk gnome-alsamixer gnome-volume-control-pulse libgconfmm-2.6-1c2 libglademm-2.4-1c2a libpulse-mainloop-glib0 libsdl1.2debian-all padevchooser paman paprefs pavucontrol pavumeter pulseaudio-module-lirc pulseaudio-module-zeroconf vlc-plugin-pulse xmms2-core xmms2-plugin-pulse
sudo apt-get install libsdl1.2debian-alsa


After a reboot, hopefully the only problem remaining is the original Line-In issue. What soundcard do you have?

---

### Post by Luffer on 2009-05-16
> **Aaardwark said:**
> If you removed pulseaudio it would have followed, they didn't specifically tell you to remove it (worst case it will tell you it's already installed): 
sudo apt-get install ubuntu-desktop


Oh, that installed something!

> **Aaardwark said:**
> 
If you want to get rid of the extra apps you installed during "sound solutions" (and get the one you lost), I've checked which ones weren't installed on my system:
sudo apt-get remove libgconfmm-2.6-1c2 libglademm-2.4-1c2a libpulse-mainloop-glib0 paman paprefs pavucontrol pavumeter pulseaudio-module-zeroconf xmms2-core alsa-oss asoundconf-gtk gnome-alsamixer gnome-volume-control-pulse libgconfmm-2.6-1c2 libglademm-2.4-1c2a libpulse-mainloop-glib0 libsdl1.2debian-all padevchooser paman paprefs pavucontrol pavumeter pulseaudio-module-lirc pulseaudio-module-zeroconf vlc-plugin-pulse xmms2-core xmms2-plugin-pulse
sudo apt-get install libsdl1.2debian-alsa


Did all that, it seemed to work.

> **Aaardwark said:**
> 
After a reboot, hopefully the only problem remaining is the original Line-In issue. What soundcard do you have?

Right, we have progress! I now only have the one volume control.... but it still doesn't do anything :( Turning it up and down and muting it has zero effect. The audio works though and I can control it with the physical volume control I have on the speakers.

Soundcard is a Sounblaster Audigy 7.1 though only left and right speakers seem to be working at the moment.

---

### Post by Aaardwark on 2009-05-16
Great! I love progress! :D

The ubuntu-desktop thing saved you from bad things next dist-upgrade, your lucky my ex-girlfriend tried removing pulseaudio once.

Before checking anything else... could you right click the sound icon, choose preferences, check that the icon controls your soundcard.

Did all speakers work before you uninstalled things? Are you sure all speaker don't work, or could it be that you didn't use sound involving all speakers. (If you have surround and not 4 speaker stereo, rear speakers should not sound all the time.)

I would also like a bit more info on your sound card. What's the output of:
lsmod | grep snd

---

### Post by Luffer on 2009-05-16
> **Aaardwark said:**
> Great! I love progress! :D

Me too :p

> **Aaardwark said:**
> The ubuntu-desktop thing saved you from bad things next dist-upgrade, your lucky my ex-girlfriend tried removing pulseaudio once.

I would personally like to thank you ex-girlfriend... do you have her number ;) LOL

> **Aaardwark said:**
> Before checking anything else... could you right click the sound icon, choose preferences, check that the icon controls your soundcard.

Not sure what you mean here. I right click the icon and select Preferences. What icon am I checking now? I just see a "Select the device and track to control" and there is a drop down list with loads of entries.

> **Aaardwark said:**
> Did all speakers work before you uninstalled things? Are you sure all speaker don't work, or could it be that you didn't use sound involving all speakers. (If you have surround and not 4 speaker stereo, rear speakers should not sound all the time.)

Errr..... possibly.... not sure how I can test all the speakers. I'm not sure if they did before or not to be honest. I need a convenient sound test utility that will output to each speaker to confirm this.

> **Aaardwark said:**
> I would also like a bit more info on your sound card. What's the output of:
lsmod | grep snd

```
snd_hda_intel         435636  3 
snd_ca0106             39968  3 
snd_seq_dummy          10756  0 
snd_ac97_codec        112292  1 snd_ca0106
snd_usb_audio          90400  1 
snd_usb_lib            24320  1 snd_usb_audio
snd_seq_oss            37760  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_midi           14336  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            29696  3 snd_ca0106,snd_usb_lib,snd_seq_midi
snd_pcm                82948  6 snd_hda_intel,snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_hwdep              15108  1 snd_usb_audio
ac97_bus                9856  1 snd_ac97_codec
snd                    62628  26 snd_hda_intel,snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device,snd_hwdep
soundcore              15200  1 snd
snd_page_alloc         16904  3 snd_hda_intel,snd_ca0106,snd_pcm

```

---

### Post by Aaardwark on 2009-05-16
> [QUOTE]Before checking anything else... could you right click the sound icon, choose preferences, check that the icon controls your soundcard.
Not sure what you mean here. I right click the icon and select Preferences. What icon am I checking now? I just see a "Select the device and track to control" and there is a drop down list with loads of entries.[/QUOTE]

"Select the device and track to control" is your cue for using the drop down list to choose your sound card. You get to choose what device the icon (along with sound buttons on keyboard) that you want to control. If you're unsure of which one it is, try one at the time to see which one works with mute. If you find the relevant one your icon will work again! :)

I got lucky on the surround bit, seems to be off standard (but easy to start), check this guide:
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)


If this works it's only Line-In left. I'll look around a bit.

---

### Post by Aaardwark on 2009-05-16
If you get the sound icon to work, could you check Sound Icon -> Open Volume Control, and see if line-in is muted or at an unreasonably low volume.

What did you do to discover Line-In didn't work?

---

### Post by Luffer on 2009-05-16
Okay, the icon controls the sound again now that I've set the device to:

```
Playback: CA0106 - CA0106 (PulseAudio Mixer)
```

Awesome, I've also got surround sound working with that test. All speakers fully functional!

As you say, just need to figure out why audio to the line-in isn't working now then it's all done.

---

### Post by Luffer on 2009-05-16
> **Aaardwark said:**
> If you get the sound icon to work, could you check Sound Icon -> Open Volume Control, and see if line-in is muted or at an unreasonably low volume.

When I go to "Volume Control..." all that I can see is the "Master" volume slider, nothing else there.

> **Aaardwark said:**
> What did you do to discover Line-In didn't work?

I route my Xbox 360's audio through the sound card so I can play games on my PC's monitor. In WinXP it works perfectly so I know the setup on the hardware side is all fine.

---

### Post by paradigm2 on 2009-05-16
> **Luffer said:**
> 
As you say, just need to figure out why audio to the line-in isn't working now then it's all done.

```

sudo apt-get install gnome-alsamixer

```

Check to see if there are check boxes for your line in and also check if it is muted.  You may need to experiment a bit.

---

### Post by Luffer on 2009-05-16
> **paradigm2 said:**
> ```

sudo apt-get install gnome-alsamixer

```

Check to see if there are check boxes for your line in and also check if it is muted.  You may need to experiment a bit.

YES!!!!!!! VICTORY! \\:D/

I don't know how you did it, but it's all working!

:KS:KS:KS:KS:KS

Got a little concerned at first because the line-in was horribly distorted, pulled it back to about 60% though and it's fine. Had to then balance everything else with it because all PC sound was far too loud in comparison. Think I've nailed it now, thank you so very, very much!

---

### Post by Aaardwark on 2009-05-16
Try installing gnome-alsamixer. Afterwards you should be able to launch it by pasting "gnome-alsamixer" into the terminal. Look for anything that says Line-In och mic. Check that it's not muted or sound volume set low.

If this works, it was probably all you had to do to solve you initial problem. But you have to agree it's handy solving other problems on the way and learning how things work.

---

### Post by Aaardwark on 2009-05-16
:KS:KS:KSCongratulations:KS:KS:KS

Have fun with your Line-In and surround! ):P

---

### Post by Luffer on 2009-05-16
> **Aaardwark said:**
> Try installing gnome-alsamixer. Afterwards you should be able to launch it by pasting "gnome-alsamixer" into the terminal. Look for anything that says Line-In och mic. Check that it's not muted or sound volume set low.

If this works, it was probably all you had to do to solve you initial problem. But you have to agree it's handy solving other problems on the way and learning how things work.

Haha, someone else swooped in and stole you thunder right at the end. I didn't realise it wasn't you, hadn't paid attention to the poster. Obviously all that praise was aimed at you. Although my thanks to paradigm2 as well of course!

---

