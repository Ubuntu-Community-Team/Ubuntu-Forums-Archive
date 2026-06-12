---
title: "Sound working for limited time, then goes mute"
date: 2009-06-10
forum: General Help
---

### Post by mbolo on 2009-06-10
Hi there,
I have Ubuntu 9.04 on a Dell Precision M4400.
All updates installed.
Nvidia proprietary driver installed.

I have a strange problem: everything is working OK except that, for some mysterious reasons, the sound is working for a random and limited (normally < 1 hour) time. Then it goes completely MUTE.
Is there something that I could do to diagnose this situation?

Thank you

---

### Post by blueridgedog on 2009-06-10
I too have sound that works great, but it randomly stops.  I have to reboot to get it to work again.  It has not gotten to the point where I have dug into it, but it appears to be tied to Firefox and flash videos.  

Here is a bug that is similar:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/183917](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/183917)

I have never put together an exact string of events that leads to it breaking down.

---

### Post by mbolo on 2009-06-10
> **blueridgedog said:**
> I too have sound that works great, but it randomly stops.  I have to reboot to get it to work again.  It has not gotten to the point where I have dug into it, but it appears to be tied to Firefox and flash videos.  

Here is a bug that is similar:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/183917](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/183917)

I have never put together an exact string of events that leads to it breaking down.

The strange thing is that I'm not using flashplugin-nonfree, but adobe-flashplugin.
And I also tried the experiment (2 youtube videos+rythmbox) and it works as expected.

---

### Post by blueridgedog on 2009-06-10
Agree...I can't force it to reappear as well, but I only posted it in case it got you thinking.  It is pretty much my only bug and the only reason I reboot.

---

### Post by mbolo on 2009-06-10
> **blueridgedog said:**
> Agree...I can't force it to reappear as well, but I only posted it in case it got you thinking.  It is pretty much my only bug and the only reason I reboot.

I think that the problem is caused by Skype.
Do you use skype?

---

### Post by blueridgedog on 2009-06-10
Nope.  Just MP3's and audio books along with firefox videos.

---

### Post by mbolo on 2009-06-10
> **blueridgedog said:**
> Nope.  Just MP3's and audio books along with firefox videos.

Which soundcard do you have?
Do you use a nvidia proprietary driver?

---

### Post by blueridgedog on 2009-06-10
I use the nvidia driver, and my sound card is the generic intel build onto asus motherboards.

Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

I have a new Omega Striker 7.1 in a box that I may try.

[http://www.htomega.com/striker.html](http://www.htomega.com/striker.html)

---

### Post by fermin on 2009-06-11
Bingo! I have this exact same problem (and it is driving me nuts)!: watching flash videos in firefox... works great for a while... then suddenly, for no apparent reason, it makes a quick strange distorted noise and completely mutes! Flash video continues to work but with no sound. I have to go out and in again to my session and it works again (no reboot needed).

I noticed this started happening shortly after I upgraded to Jaunty, since it never happened before. Both my sound card and video card are Intel integrated into the motherboard of my laptop.

Also since the upgrade to Jaunty (approximately) some flash animations and videos start to flicker randomly, which is sometimes really annoying.

Out of curiousity I typed dmesg into the terminal and this is what I get in the last line:
```
 hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
```My sound hardware (from lshw) is:
```
*-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```I tried, reinstalling the adobe flashplugin non-free and the problem continued. I switched to the flash plugin provided by the Ubuntu MOTU team (I dont know if this comes in the standard Ubuntu repositories since I also have the Medibuntu repostory activated) but the problem stayed the same. None of the two flash plugins seemed to work better nor make any difference.

I have no other troubles listening to music in music files with Amarok or other players. In fact, OOOh IMPORTANT: SOUND ONLY MUTES FOR FLASH VIDEOS, that is, after the flash sound completely mutes, I can still hear sound from any other source like my music files or the Ubuntu sound effects, which work OK.

I could switch to Gnash but it is still limited and, although I am very much interested in Gnash's development, it is not yet completely functional.

Any clues?

---

### Post by blueridgedog on 2009-06-11
My sound died today while I was at work, I had Pandora playing this am, paused it when I went to work and when I came home the sound system was dead...a reboot fixed it, but I still can put a finger on the issue.  I too can't mute the sound.  I suspect a new card is in order.

```
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

---

### Post by Terry32 on 2009-06-22
I had a similar issue with my Dell Precision M4400 on Kubuntu 9.04, I opened the sound mixer and noticed one of the sliders was all the way at the bottom, I moved it back to the top and the sound returned. Before I discovered that I would have to reboot to make it come back.

---

### Post by anomenat on 2009-07-08
I have the same problem. (Or at least a very similar one.) It is now my only major gripe with Linux, everything else appears to work fine.

I have a Lenovo Thinkpad X200, which has an Intel audio device like the earlier posters in this thread.

The symptoms are that sometimes my audio is muted and I cannot unmute it. I've checked all the volume levels that I can find (ALSA and PulseAudio) and they are correct - it doesn't appear to be a problem with mixer levels.

The muting is specific to the Intel sound device - audio still works fine over a USB sound device.

I used to reboot to fix the problem but I've since discovered that restarting Firefox will fix it. So I think it is something to do with Firefox. I'm not convinced that it is the flash plugin that's at fault: does the plugin do something even if you don't load a webpage with flash in it? My audio is often muted even if I don't view flash webpages.

---

### Post by blueridgedog on 2009-07-08
I too followed the flash threads, but I have verified that the audio stops randomly and items that play audio then are in a odd state (totem will simply launch to a gray screen when double clicking an mp3).

---

### Post by sdowney717 on 2009-07-08
you can try getting rid of pulse audio and using alsa only.
check into how to do this, I had trouble with audio quitting on intrepid and upgrading to jaunty sound has not quit ever. But I was told it was related to pulse audio.

---

