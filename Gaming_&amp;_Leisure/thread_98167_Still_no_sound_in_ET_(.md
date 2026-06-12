---
title: "Still no sound in ET :("
date: 2005-12-02
forum: Gaming &amp; Leisure
---

### Post by Daandaan on 2005-12-02
I've tried a lot of things to have sound in Enemy territory (2.6) but I still have no sound. Apps like Xmms and totem produce sound but there's no sound in ET! I use Open Sound System. Should I change this? Alsa works too for Xmms and other apps.
Greetz Daan

P.S sound works for tux racer

---

### Post by Cyhatch on 2005-12-03
Yes. :) (Try ALSA.)

(Also, isn't there an [FONT="Courier New"]esd[/FONT] runnig accidentally?)

---

### Post by Daandaan on 2005-12-04
I switched to ALSA and I did a sudo killall esd, started ET, but no sound...:(

---

### Post by easy_target on 2005-12-04
[QUOTE=Drummer]I put this in the file /etc/init.d/bootmisc.sh (at the end, before ": exit 0") to get sound working in et, without having to run it as root. Putting it in this file just makes sure that it's run when the computer boots, otherwise you'd need to run that command in a terminal as root (not just with sudo) each time you reboot.

```
#sound for et echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

```
I've also experienced problems with permissions, especially when et downloads extra .pk3 files, I fixed this by doing this:

```
#sudo chown -R user:user /usr/local/games/enemy-territory 
#sudo chown -R user:user ~/.etwolf

```
where user is your username. This happened when running et as a normal user, you may not have this problem, but here's my fix if it does happen.
:([/QUOTE]

Found it on a post in [THIS]("http://www.ubuntuforums.org/showthread.php?t=83028&highlight=enemy+territory") thread.
Hope this helps.

---

### Post by ulisse on 2005-12-04
Try to edit the file:
~/.etwolf/etmain/profiles/{YOUR_PROFILE_NAME}/etconfig.cfg

find the row that says:
seta snddevice "/dev/dsp"

and change to:
seta snddevice "/dev/adsp"

(you have to already have ALSA set up, take a look [HERE]("http://ubuntuforums.org/showthread.php?t=44753") if not)

---

### Post by Zimmer on 2005-12-04
Here is the Help file I wrote for myself to get Sound going on Hoary..
It worked in Breezy, too...
You may have sound related problems.......
Some of the ways to cure them...

(For Ubuntu )make sure gstreamer defaults are set to alsasink and alsasrc
then in Terminal..

killall -9 esd
....I do not do that anymore as I have re configed ESD as follows:-
(the exact file is  /etc/esound/esd.conf )

[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 5



..******....but I still do this at a Terminal to get it to produce sound....*******

sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'

**note the exact use of single and double quotes in the example above***
or try
esddsp --mmap et (did nothing for me..)

make sure gstreamer defaults are reset to esdsink and osssrc after playing if you changed them earlier ...or your sound for other stuff might be compromised..(only might..)

 Run ET from a terminal and then if it doesn't work look at the output text in the terminal window to get a clue as to why it won't sort the sound module..
Regards.
Zimm

---

### Post by Daandaan on 2005-12-11
That helped! Thx:)

---

