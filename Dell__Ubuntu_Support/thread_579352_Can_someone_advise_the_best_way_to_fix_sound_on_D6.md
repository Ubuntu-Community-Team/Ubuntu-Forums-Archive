---
title: "Can someone advise the best way to fix sound on D630/830"
date: 2007-10-18
forum: Dell  Ubuntu Support
---

### Post by garymansell on 2007-10-18
Please can someone advise me the preferred method of fixing the sound on my D630 with Gutsy.

I ask this because I presume that this will be officially fixed sometime soon (any ideas when)???? and when it is I don't want to have any issues with the previous fix that I applied.

It seems to me that perhaps the best thing to do is a custom 2.6.23 kernel from kernel.org as I understand that this will fix the problem. A custom kernel can easily be removed when a proper fix is released.

Any suggestions welcome

Rgds

Gary

---

### Post by NilsE on 2007-10-18
You did not say what the problem is but try these steps and see if it helps

In a terminal run: asoundconf list

This should return a list of cards.  Yours should be Intel

In a terminal run: asoundconf set-default-card Intel

Then again with sudo: sudo asoundconf set-default-card Intel  

This will set the defaults for the card and create a config file. If yours is not Intel replace it with the name you found in list.

In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice except mixer should be Sigmatel.

In the volume control turn on as many options as you can to show up in the panel. Make sure none are muted.

---

### Post by garymansell on 2007-10-18
asoundconf list shows no sound cards

---

### Post by Rocketmac on 2007-10-18
> **garymansell said:**
> asoundconf list shows no sound cards

What is the output of 'lsmod | grep oss'?


It should look something like this:

> 
Rocketmac@Archimedes:/home/Rocketmac$ lsmod | grep oss
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            33152  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device


---

### Post by NilsE on 2007-10-18
Here is also a good tutorial on getting sound cards working.  

[http://ubuntuforums.org/showthread.php?t=205449&highlight=activate+sound+card](http://ubuntuforums.org/showthread.php?t=205449&highlight=activate+sound+card)

---

### Post by Razzoo on 2007-10-18
For 32bit Gutsy, the following may get your card recognised 
[http://ubuntuforums.org/showthread.php?t=564581&highlight=82801h]("http://ubuntuforums.org/showthread.php?t=564581&highlight=82801h")

> sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

REBOOT

It comes with quirky headphone-speaker  behaviour -- try booting with and without the headphone jack in.

---

### Post by sampan74 on 2007-10-18
> **NilsE said:**
> Here is also a good tutorial on getting sound cards working.  

[http://ubuntuforums.org/showthread.php?t=205449&highlight=activate+sound+card](http://ubuntuforums.org/showthread.php?t=205449&highlight=activate+sound+card)

That guide solved my problems with sound problems on a HP Compaq nw9440 after upgrading to 7.10 Gutsy Gibbons. The nw9440 uses the snd-hda-intel driver on a  Intel 82801G (ICH7 Family) chipset.

Thanks a bunch NilsE!

---

