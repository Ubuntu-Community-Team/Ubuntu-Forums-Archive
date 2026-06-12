---
title: "No Low Volumes"
date: 2012-05-22
forum: Desktop Environments
---

### Post by ygallup on 2012-05-22
I recently installed a clean copy of 12.04. So far everything has worked reasonably well, but I have a problem with the volume. Unless I have the volume at 1/4, or above I don't get any sound. Above that the sound control is quite precise, but If I want the volume to be any lower (which I often do), I have to adjust the volume on the individual application I am using. At one quarter the sound comes in relatively loud, all at once. This makes it thoroughly frustrating to adjust volume on a whim.

---

### Post by ygallup on 2012-05-23
Any ideas anyone? It is an extremely annoying problem.

---

### Post by corrosion190 on 2012-07-21
I have the same problem but at 3/4.

---

### Post by Frogs Hair on 2012-07-21
I notice many different levels with video and music and that is due to who, when, and how the media was produced. I think there is or was software/plugin to remedy this. My system sounds are consistent so I know the media is culprit.

---

### Post by jmfal on 2012-07-21
+1  To frogs hair

your lucky that you have full volume
There are others that are set to full volume and can't here a thing
I have the same problem from one song or format to the next
IN windows or ubuntu, I have the same problems, you'll just have to adjust to it.

There is a way to edit a file that limits volume output but sooner or later you'll have problems with that.
Just like me or a lot of others you'll just have to get used to adjusting the volume, especially when switching formats.

---

### Post by madeinfamous on 2012-07-22
allo,

I feel like helping you this morning... so enjoy!


Volume range anomalies

The latest version of PulseAudio tries to control the volume of the sound card using its mixer controls. Usually this works just fine, but in some cases this does not work properly.

Diagnosis

You experience any of the following:

Jumps in volume, e g if everything below 20% is muted, and 21% is very loud. Overdriven (distorted sound) if the volume is set above a certain (low) level No volume changes in parts of the range, e g if 20% is just as loud as 70%.

Fix / Workaround

There are a few variables which control how PulseAudio controls the volume. You can either edit /etc/pulse/default.pa (you'll have to be root to do that) to change the behavior for all users, or copy that file to ~/.pulse/default.pa and then edit that file, to change behavior for the current user only.

[you know it's easy: gksu gedit /etc/pulse/default.pa]

Open the file mentioned above. Find the row saying "load-module module-udev-detect" and change it to:

load-module module-udev-detect ignore_dB=1

To try your changes, restart PulseAudio with the following command:

killall pulseaudio

PulseAudio will then autospawn (restart itself).

You may find that the above workaround is insufficient, in which case you may configure PulseAudio to control only one mixer control, e.g., PCM (cf. alsamixer). Find the row saying "#load-module module-alsa-sink" and change it to:

load-module module-alsa-sink control=PCM

(remember to remove the # in the beginning of the row!) Optionally replace PCM with the mixer control you want PulseAudio to control.

You will then need to killall pulseaudio as above and allow the daemon to autospawn.

---

