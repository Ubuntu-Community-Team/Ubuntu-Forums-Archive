---
title: "TeamSpeak and RTCW:ET with poor sound card"
date: 2005-11-09
forum: Gaming &amp; Leisure
---

### Post by ulisse on 2005-11-09
Hello Tribe!
I've had some troubles getting to work together Enemy Territory and TeamSpeak on my AC97 sound card.
The problem is that TeamSpeak does not support ALSA, and the card doesn't support hardware mixing.
After a lot of googling, I found [this]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=34") howto that worked for me.
I think it is a dirty way, but it works and doesn't mess up the system: if something goes wrong, just reboot (in m$ windows style) and everything wil revert back to the original status.

Assuming that you have set up right your ALSA (see [here]("http://ubuntuforums.org/showthread.php?t=44753&highlight=teamspeak") to learn how), this is shortly what you have to do:

**1.** check if your card supports at least two devices, one in capture/playback and one in playback only:
```
ulisse@Dante:~ $ cat /proc/asound/pcm
00-00: VIA 8237 : VIA 8237 : playback 4 : capture 1
00-01: VIA 8237 : VIA 8237 : playback 1 : capture 1
```
(in this case i have two capture/playback devices)

**2.** you have to remove your default audio device and recreate it as dsp0:
```
sudo rm /dev/dsp
sudo mknod /dev/dsp0 c 14 3

```
you should already have an "adsp" or "adsp0" device; if not, create it:
```
sudo mknod /dev/adsp 14 12

```

**3.** change the permissions and owners of the new device(s):
```
sudo chmod 660 /dev/dsp0
sudo chmod 660 /dev/adsp
sudo chown root.audio /dev/dsp0
sudo chown root.audio /dev/adsp
```

**4.** create a "dsp" symlink to the adsp device:
```
sudo ln -sf /dev/adsp /dev/dsp

```

**5.** write something to tell the systema that RTCW:ET doesn't need the mic:
```
sudo -s  #(you need to be root to issue this commands)
echo "et.x86 0 0 direct">/proc/asound/card0/pcm1p/oss
echo "et.x86 0 0 disable">/proc/asound/card0/pcm1c/oss
exit  #(to return to your user)

```

**6.** crate a symlink /dev/dsp to the playback device.
```
sudo ln -sf /dev/dsp1 /dev/dsp
```

**7.** open TeamSpeak and set it to use "/dev/dsp0" as device, apply, close and reopen it in this way:
```
esddsp -m TeamSpeak
```

Now you should run Enemy Territory and talk to your team together!



You will have to issue all this commands every time you reboot, so for convenience I have put all that stuff in a script to be run just before playing:
```
#!/bin/bash
if [ "`whoami`" != "root" ]; then
echo "you must run this script as root!"
exit 1
fi
rm /dev/dsp
mknod /dev/dsp0 c 14 3
chmod 660 /dev/dsp0
chown root:audio /dev/dsp0
ln -sf /dev/adsp /dev/dsp
echo "et.x86 0 0 direct">/proc/asound/card0/pcm1p/oss
echo "et.x86 0 0 disable">/proc/asound/card0/pcm1c/oss
ln -sf /dev/dsp1 /dev/dsp
echo "now run as user 'esddsp -m TeamSpeak'"

```

I hope it will be useful!


*disclaimer: if you have a better way to do this, why didn't you tell me before? ;) *

---

### Post by pepolez on 2006-10-01
I have the exact same soundcard as you. 

This solved my problem with TeamSpeak where the client would not pick up the microphone, which is what was bugging me most. I found I had to install esound-clients first.

However, after following this process, I was left with no sound in Enemy Territory. I was able to get sound in ET again by starting artsd and then starting ET with artdsp -m (editing et starter scripts).

Here is my ET starter script now:
```

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec artsdsp -m ./et.x86 "$@"

```

---

