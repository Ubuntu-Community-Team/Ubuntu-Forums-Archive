---
title: "Lost audio when upgrading to 8.10.  Need Help"
date: 2008-11-02
forum: Desktop Environments
---

### Post by Moondoggy on 2008-11-02
Help!

I upgraded my copy of Ubuntu from 8.04 to 8.10 tonight and when I got finished I noticed that my machine no longer has any sound.  When I press the volume control button I get the following error message:

No volume control GStreamer plugins and/or devices found.  I checked Package Manager and it looks like I have GStramer installed and I tried reinstalling it again but no change.  Everything worked fine in 8.04.

Can anyone assist a newbie with this problem?

---

### Post by Blackwolf_Oz on 2008-11-03
sudo killall pulseaudio
    sudo alsa force-reload


and them go to System>Preferences>Sound and change everything to ALSA

---

### Post by jughrin on 2008-11-08
> **legend1264 said:**
> sudo killall pulseaudio
    sudo alsa force-reload


and them go to System>Preferences>Sound and change everything to ALSA

Same problem, here.

This didn't work. Got a bunch of error stuff after the force-reload:
```
ohn@ubuntu-ughrin:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
Terminating processes: 6585lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-ice1724 snd-ice17xx-ak4xxx snd-ac97-codec snd-ak4xxx-adda snd-ak4114 snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-pt2258 snd-i2c snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-ice1724 snd-ice17xx-ak4xxx snd-ac97-codec snd-ak4xxx-adda snd-ak4114 snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-pt2258 snd-i2c snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

---

### Post by eskimoquinn on 2008-11-09
I have the same problem and the above suggestion did not work for me either.

When I force ALSA reload, I get this message:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
Terminating processes: 6331lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-intel8x0 snd-bt87x snd-ac97-codec snd-seq-dummy snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-intel8x0 snd-bt87x snd-ac97-codec snd-seq-dummy snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

---

### Post by bailunrui on 2008-11-09
This solved my sound problem! Thank you very much.

---

### Post by shimi on 2008-11-10
This might help you with your [Ubuntu 8.10 sound problem]("http://mylinuxnotebook.blogspot.com/2008/11/ubuntu-810-flash-sound-problem.html")

---

### Post by seuzy13 on 2008-11-10
I have the same problem after upgrading to Intrepid with almost the exact same ALSA error messages. The funny thing is the problem didn't arise until I restarted my computer a few times.

I should also add that when I shut down my computer and the screen gets to the shut down step regarding ALSA, it freezes, and I have to force the shut down.

---

### Post by eskimoquinn on 2008-11-10
My experience is similar to seuzy13's above.

---

### Post by legolas_w on 2008-11-11
Have you fixed your problems?
I have the same problem and the given solution does not works.
I should say that there are seveal items in sound setting which has ALSA keyword, like Intel HDA Analog, Intel HDA digital, and so on, which one I should choose?
thanks

---

### Post by seuzy13 on 2008-11-11
After doing some digging around, I believe this is the bug report for my problem (and perhaps yours as well):
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361)

It's some sort of issue with gvfs, I think (due to the error messages), and it has not been fixed yet. If no one else knows what to do, all I can think of is to sit tight until the bug is fixed. =/

---

### Post by ZiplocBag on 2008-11-11
> **legend1264 said:**
> sudo killall pulseaudio
    sudo alsa force-reload


and them go to System>Preferences>Sound and change everything to ALSA

Ack, didn't work for me either. Instead I get:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jmoufarrege/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jmoufarrege/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

---

### Post by legolas_w on 2008-11-12
I just wanted to bump the thread up.
I have no audio and it is going to be problematic for me as I can not use Skype.

---

### Post by shockwaves59 on 2008-11-12
**** **** VAGINAL UNTERSUSSjaeorgjaoiejrtgoiajrogijaoerigjaoerjigiaejgoaerjg BAN ME LOPLOLOLEGopaejkro;gjiae;gjaeriog


also
ANAL RAPING CTATSTA

---

### Post by seuzy13 on 2008-11-12
I think the thread needs yet another bump. 

I posted the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361") for this earlier, and apparently the people have figured out a work around for the problems, but I don't know how to implement it. Anyone with just a little bit more knowledge than me would probably understand how to do it. I also left a comment just to ask how I could work it out, but if you're reading this thread, please take a look and see if you can make anything out of it. This bug is really annoying for me and a bunch of others, I'm sure.

---

### Post by psyke83 on 2008-11-12
PulseAudio is not configured properly on your systems (possibly due to cruft from Hardy).

Follow steps 2-5 of [this]("http://ubuntuforums.org/showthread.php?t=866965") guide, and everything should work fine.

N.B. If you have multiple sound cards or attached USB/Bluetooth headphones, PulseAudio may select them as the default. Keep it in mind if you think you're getting no audio.

If you've got multiple cards, go to the PulseAudio Volume Control (pavucontrol, available after following the guide), Output Devices, and right-click on your desired card to become default, and check the "Default" option. Also delete the ~/.pulse/volume-restore.table to reset the previous application settings (as they will otherwise continue to choose the old output device).

---

### Post by seuzy13 on 2008-11-12
> **psyke83 said:**
> PulseAudio is not configured properly on your systems (possibly due to cruft from Hardy).

Follow steps 2-5 of [this]("http://ubuntuforums.org/showthread.php?t=866965") guide, and everything should work fine.

N.B. If you have multiple sound cards or attached USB/Bluetooth headphones, PulseAudio may select them as the default. Keep it in mind if you think you're getting no audio.

If you've got multiple cards, go to the PulseAudio Volume Control (pavucontrol, available after following the guide), Output Devices, and right-click on your desired card to become default, and check the "Default" option. Also delete the ~/.pulse/volume-restore.table to reset the previous application settings (as they will otherwise continue to choose the old output device).

I had already followed this how-to earlier, and I still have the problem. Also, when I try to open any of the dialog boxes from the PulseAudio Volume Control, I get the message: "Connection failed: Connection refused." And also, I have no idea if I have multiple sound cards. 

I had been using my headphone jack to output sound through my stereo, but whenever I tried, I couldn't get sound out of it either.

---

### Post by seuzy13 on 2008-11-13
Okay, after some digging around, I typed in a command, which I don't recommend trying yourself, because I have no idea if it had any harmful effects. In any case, this command removed the warning message from my "sudo alsa reload" command, and I believe it reloaded successfully, but my audio is still gone. The command I used was:
$ fusermount -u /home/myusername/.gvfs
This DID get rid of the error message, but it was helpful in no way to getting my audio back.

---

### Post by seuzy13 on 2008-11-13
My apologies for the triple post, but after *yet another* restart, I can open the PulseAudio Volume Control. It looks like I have only one sound card (only one listed as an option). Under the Output tab, this one sound card, has a mute icon beside it. When I click the mute icon, the rest of the menu grays out. When I click it again the menu goes back to normal, but the mute icon never turns to a normal "sound is on" icon. This sound card *is* selected as default, by the way.

Under the applications tab, it *does* list applications that are currently playing sound, but there is the same situation with the mute icon. Also, strangely, the two sliders are all the way to the right, but it says 0.00 dB beside them. When I move them farther to the left, I get negative decibel numbers.

---

### Post by seuzy13 on 2008-11-13
I know this makes the fourth post in a row, but I have fixed the problem!

$ sudo apt-get install gnome-alsamixer
$ gnome-alsamixer

I checked the box "IEC958." I also unmuted everything and moved the sliders up, but I think checking the box is what did the trick.

This is the fix! :)

---

### Post by ZiplocBag on 2008-11-14
Didn't seem to work for me. I can't open the Sound Card preferences up. All that happens is that Gnome-Alsamixer closes down.

---

### Post by seuzy13 on 2008-11-14
Hm...did you also follow the guide that psyke83 posted? Otherwise, I really have no idea what could be done. =/

---

### Post by ZiplocBag on 2008-11-15
> **seuzy13 said:**
> Hm...did you also follow the guide that psyke83 posted? Otherwise, I really have no idea what could be done. =/

Nope, didn't work. >_<

---

### Post by seuzy13 on 2008-11-15
Really sorry. Don't know what to tell you then. Hopefully someone else will come along who has the answers. =)

---

### Post by alwayshere on 2008-11-15
this is the question with no awnser i get my sound working then a week later it craps out only to work agaian on a bunch of settings that never worked before we need some sort of super nerd to help out here .

maybe going back to esound might work i have tried but 8.10 seems to need pulse audio to start gui buggerd if i know.

---

### Post by ZiplocBag on 2008-11-22
Bump? It's still crap.

---

