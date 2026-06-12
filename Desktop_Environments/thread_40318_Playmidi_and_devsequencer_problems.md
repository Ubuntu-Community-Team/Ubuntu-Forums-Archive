---
title: "Playmidi and /dev/sequencer problems"
date: 2005-06-08
forum: Desktop Environments
---

### Post by erik-the-red on 2005-06-08
When I do "playmidi -a 1e.mid" on xterm, it says

*open /dev/sequencer: No such file or directory.*

How can I play midi files using my SB Live! sound card?

---

### Post by erik-the-red on 2005-06-09
Bump

---

### Post by erik-the-red on 2005-06-10
Bump

---

### Post by skoal on 2005-06-10
snd-seq is the module you want to insert:

```
skoal@morpheus:///tmp $ sudo modprobe snd-seq
```
should do it.  That'll make your /dev/snd/seq the application is looking for...

\\//_

---

### Post by erik-the-red on 2005-06-10
[QUOTE=skoal]snd-seq is the module you want to insert:

```
skoal@morpheus:///tmp $ sudo modprobe snd-seq
```
should do it.  That'll make your /dev/snd/seq the application is looking for...

\\//_[/QUOTE]
 Skoal, thanks for the reply!

Now, it says:

```

playmidi: No playback device found.

```

---

### Post by aaroniu on 2005-06-13
I've had the same problems as erik-the-red and am at the same point. Anyone have ideas or links to a good resource for configuring midi on Linux?

---

### Post by skoal on 2005-06-13
hmm...

I've never used "playmidi" before, but the /dev/midi device should already be present.  I looked at the permissions and != access for non-root users.  Try:

sudo playmidi <nowdamnit!>

* substituting "nowdamnit!" with the appropriate (and real) midi filename.

If that don't work as sudo, I was just checking the other modules you could possible load for this app (and I'm taking a wild guess that you even need to since I don't have it installed myself), but:
```
skoal@morpheus:///lib/modules/2.6.10-5-686/kernel $ find . -name *midi*
./sound/oss/v_midi.ko
./sound/core/seq/snd-seq-midi.ko
./sound/core/seq/snd-seq-virmidi.ko
./sound/core/seq/snd-seq-midi-event.ko
./sound/core/seq/snd-seq-midi-emul.ko
./sound/core/snd-rawmidi.ko
./sound/drivers/snd-virmidi.ko
./drivers/usb/class/usb-midi.ko
```
shows several other possible modules you can try to load - for example:

sudo modprobe snd-seq-midi
sudo modprobe snd-seq-virmidi
[...]
sudo modprobe snd-rawmidi
etc.

I don't know what else it could be without installing that app.

\\//_

---

### Post by eeclark on 2005-12-12
sudo playmidi -e Frosty_The_Snowman.mid


the above worked for me

-e pipes it to "External MIDI"


playmidi -e Frosty_The_Snowman.mid

also worked

Using a USB MIDI port on a Dell Latitude D800 (Ubuntu 5.10)

---

