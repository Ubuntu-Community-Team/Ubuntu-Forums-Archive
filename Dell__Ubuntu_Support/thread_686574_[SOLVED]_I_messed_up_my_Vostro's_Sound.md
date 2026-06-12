---
title: "[SOLVED] I messed up my Vostro's Sound"
date: 2008-02-03
forum: Dell  Ubuntu Support
---

### Post by toneman77 on 2008-02-03
Hi
I have a Dell Vostro 1400 and after some tweaking everything went smoothly. Everything except the microphone.#Somewhere i red that the Vostro is almost the same hardware as the 1420 and so I followed[ this guide]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work") and installed *linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb*. Sadly, that  didn't help. At this point my */etc/modprobe.d/alsa-base* looked like this:
```
options snd-hda-intel model=5stack
```
I then searched again and found out, that *linux-backports-modules-generic* could solve my problem. So I installed that but that didn't help neither, so all uninstalled again.

Right now I'm at this point after a reboot to get sound:
1. sudo modprobe -r snd_hda_intel
2. change */etc/modprobe.d/alsa-base* from
```
options snd-hda-intel model=5stack
to
options snd-hda-intel model=dell-laptop
```
3. sudo modprobe snd_hda_intel
Now I have sound and can use my Volume up/down keys on my laptop.

The problem is now, when i reboot all the sound is gone and i have to
1. sudo modprobe -r snd_hda_intel
2. change */etc/modprobe.d/alsa-base* from
```
options snd-hda-intel model=dell-laptop
to
options snd-hda-intel model=5stack
```
3. sudo modprobe snd_hda_intel

Now i have sound. But it's maximum volume and my volume up/down keys have no effect. I again have to unload the module, change modprobe.d/alsa-base to *dell-laptop* and reload the module to get back my original functionality.

What has gone wrong here ?
Everything used to work excellent before I installed those backports stuff. i then had model=5stack in my alsa-base file.

Please help me out.

Greetings

Tone

---

### Post by StefAndrew on 2008-02-05
Hmm, I haven't had any problems with my sound card after installing the backports.  I didn't do anything else.  Both times have been on fresh installs before doing anything else(well, after running all updates after installing Gutsy).  And then after rebooting, I just had to make sure all volume options were checked in the sound options and then move all the volume sliders up and my sound works great.

The only change I did make after backports, but didn't seem to make any difference was to use the line:

```
options snd-hda-intel model=**3**stack
```

Like I said, I didn't notice any difference though, as my low volume problem was solved by making sure all volume sliders were on and turned all the way up.

---

### Post by toneman77 on 2008-02-05
Which backports did you install ? the ones from Dell ?

---

### Post by StefAndrew on 2008-02-05
Ok, looks like it's only found in Synaptic Package Manager.

Click System > Synaptic Package Manager.  Type you sudo password.  Click on Search.  Type in backports.  Click search.  Check the box for linux-backports-modules.  Click apply.  It should prompt you that it has dependencies to install.  Make sure you install all of the dependencies as well.  Reboot after this is done and you should be good to go.

---

### Post by toneman77 on 2008-02-06
I installed linux-backports-modules as well as its dependencies and i have sound. But my volume-up and -down keys have no effect. The volume bar moves but the volume doesn't change.
I opened up gnome-volume-control and saw that my volume buttons change the first input slider ?!

Is there a way to select which slider/device is controlled by multimedia keys ?

---

### Post by toneman77 on 2008-02-06
Found it
[https://help.ubuntu.com/community/MultimediaKeys#AssigningTracksToKeys](https://help.ubuntu.com/community/MultimediaKeys#AssigningTracksToKeys)

Thanks for the help anyways.

---

### Post by StefAndrew on 2008-02-06
Yeah, sorry I didn't get the chance to tell you yet.  It was under the sound settings under the system menu.  The selection box down at the bottom of the sound properties.  Or you can right click on the sound icon, and go to properties and pick it that way too.

Glad you got it working.

---

