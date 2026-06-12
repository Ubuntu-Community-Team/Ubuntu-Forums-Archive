---
title: "[SOLVED] No Audio after upgrade to 8.04"
date: 2008-04-27
forum: Desktop Environments
---

### Post by shimi on 2008-04-27
I can't play audio files after I upgraded to 8.04. I can't play any audio file (mp3, ogg...).
I can play audio streams using firefox but I can't play any audio files with amarok, rythembox or totem.

---

### Post by ubuntwinkel on 2008-04-27
Same here.  Upgrade from 7.10 to 8.04 (via update manager) results in no sound.  Tested all options in the sound configuration applet (System > Preferences > Sound) including autodetect, ALSA, ESD, OSS, PulseAudio, all with various error messages as follows:

Error message when testing Autodetect, ALSA, OSS, and PulseAudio:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

(Initially I thought they gave different results.)

Error message when testing ESD:
...well, this froze the sound applet, and I am posting before the whole system freezes.  Will update with PulseAudio results

(Edited above, and added following.)

I uninstalled all the gstreamer packages I could comfortably remove, without success.  I neglected to mention this is on a Dell 1420N.

---

### Post by jeffreyldavidson on 2008-04-27
I had the same problem. I have the Dell 1420N. After upgrade Hardy did not recognize the hardware. I did a complete fresh install and it worked ok...strange. However, now the media buttons do not work, so I will reinstall with Dell's ISO when it is out.

---

### Post by ubuntwinkel on 2008-04-27
It seems 8.04 cannot find a sound card...
```
$ sudo alsactl names
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 0 failed: No such device
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 1 failed: No such device
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 2 failed: No such device

```

Also, the volume control panel-thingy returns this tidbit:
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

I did have sound in 7.10.

---

### Post by ubuntwinkel on 2008-04-28
Fix found at [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)


Copy/pasted from there:
> Description: No sound after Distribution Upgrade.
Systems Affected: Inspiron E1505n, 1420n and 1525n.
Impact: No sound from speakers or headphones.
Fix: Remove old modem driver, since it does not work on Ubuntu 8.04:

```
$ sudo dpkg -r hsfmodem
```

Remove old linux-backports-modules package, which is no longer needed:

```
$ sudo dpkg -r linux-backports-modules-2.6.22-14-generic
```

Restore name of sound driver that old modem driver renamed:

```
$ cd /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda
$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
```

Remove old sound drivers from kernel module directory:

```
$ cd /lib/modules/2.6.24-16-generic/updates
$ sudo rm snd-hda-intel.ko
$ sudo rm snd-hda-codec.ko
```

Rebuild initrd and reboot:

```
$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot
```


---

### Post by shimi on 2008-04-28
Well as I wrote I can hear sounds, my sound card works. I can listen for audio streams but I can't play mp3 and ogg files

---

### Post by shimi on 2008-04-28
Well as I wrote I can hear sounds, my sound card works. I can listen for audio streams but I can't play mp3 and ogg files

---

### Post by Mc_Lovin on 2008-04-29
I have the same problem.  I just upgraded today.  I can listen to audio through firefox but I can't play a file off my hd.
Totem hangs and VLC runs but there is no sound.  Video files will play but there will be no audio behind it.

---

### Post by novus721 on 2008-04-29
I have the same problem, though my messing around with it has now caused an endless static sound whenever I power up my speakers

---

### Post by shimi on 2008-05-07
The problem was fixed after today update

---

### Post by joshuars on 2008-05-07
> **Mc_Lovin said:**
> I have the same problem.  I just upgraded today.  I can listen to audio through firefox but I can't play a file off my hd.
Totem hangs and VLC runs but there is no sound.  Video files will play but there will be no audio behind it.

I too have this problem.  Using a TP T42.

---

### Post by shimi on 2008-05-11
I was wrong. It seems to work only if the audio player is the first application I start.
I am using ThinkPad T61

---

### Post by carib909 on 2008-06-18
I have audio with headphones, but I cannot get audio from my speakers anymore. I get audio from speakers when Ubuntu boots up, but streaming audio and MP3's are silent.

---

### Post by shimi on 2008-07-21
After a long time, I managed to solve the problem. I needed to install libflashsupport.

[http://mylinuxnotebook.blogspot.com/2008/07/ubuntu-sound-flash-problem.html](http://mylinuxnotebook.blogspot.com/2008/07/ubuntu-sound-flash-problem.html)

---

