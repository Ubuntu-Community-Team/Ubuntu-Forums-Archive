---
title: "No sound with flash in 9.04"
date: 2009-05-03
forum: General Help
---

### Post by Lil Jimmy on 2009-05-03
I'm sure many of you have had this problem, because a quick google search gave many relevant results. It's pretty simple, really: I try to watch flash videos with Firefox but there's no sound that comes out. I have had this same problem with 8.04, I believe, but it was fixed in 8.10.

I have tried to remove the flashplugin-nonfree package then reinstalling it again. I purged it even. No avail.

Is there someone who has an alternate possible solution? Thanks.

---

### Post by linux_djc on 2009-05-03
uninstall and purge it again, and attempt to install it from the adobe flash website

---

### Post by Lil Jimmy on 2009-05-03
I did the following:

```
sudo apt-get --purge remove flashplugin-nonfree
sudo apt-get --purge remove flashplugin-installer
sudo apt-get install flashplugin-installer
sudo apt-get install flashplugin-nonfree
```

Then restarted Firefox, but it's still not working.

---

### Post by kostkon on 2009-05-03
Does it happen that you have two sound cards in your system? If you are not sure, please open a terminal and give the following command
```
aplay -l
```
and post its output here.

---

### Post by Lil Jimmy on 2009-05-03
```
**** List of PLAYBACK Hardware Devices ****
card 0: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, yeah, I'm trying to get sound through my USB headset.

---

### Post by kostkon on 2009-05-03
> **Lil Jimmy said:**
> ```
**** List of PLAYBACK Hardware Devices ****
card 0: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, yeah, I'm trying to get sound through my USB headset.

OK. Then You need to install the *PulseAudio Device Chooser* utility from *Synaptic*. When you run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

From there you will be able to select the default card for input and output. In the *Output Devices* tab you should see your USB headset listed. Just right-click on it and enable the *Default* option to set it as the default output device, if you want.

If after doing the above you are not getting audio from *Flash* through your USB headset, or if you don't want to set your USB headset as the default output device but only to use it for *Flash*, then the thing you need to do is, first of all, to put a *Flash* video *playing* in Firefox. Then open the *PulseAudio* volume control again and select the *Playback* tab.

There you should see the audio stream of the *Flash* video listed. Right-click on it and select *Move Stream...* and in the list that will appear select your USB Headset. *PulseAudio* should remember your choice from now on.

For this to work you'll need to set your sound playbacks (i.e. for Sound Events, Music and Movies, as you said) in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*. You can do the same for your inputs, set them to *Autodetect*, if you have specified an input device in the *PulseAudio Device Chooser*, for example your ATI sound card.

Hope that helps.

---

### Post by Ansible on 2009-05-03
> **Lil Jimmy said:**
> I have had this same problem with 8.04, I believe, but it was fixed in 8.10.

I have tried to remove the flashplugin-nonfree package then reinstalling it again. I purged it even. No avail.

Is there someone who has an alternate possible solution? Thanks.

I had this problem after an upgrade to 8.10 from 8.04.  Just on my laptop though, my other machines didn't have the problem.  For this reason and some other glitches after the upgrade, I decided to do a clean install of 9.04.  

After the install, I copied over my .mozilla folder from my old /home directory.  Interesting thing #1: flash worked in firefox without having to install it.  Interesting thing #2: still no sound from flash!  

My solution was to remove my old .mozilla folder and replace it with the default one from 9.04 (which I had backed up).  Then when I went to a website with flash, it said no flash was installed - which I would have expected on a fresh ubuntu install anyway.  I installed flash from the synaptic package manager and it now works with sound.

---

### Post by tinker123 on 2009-05-03
> **kostkon said:**
> OK. Then You need to install the *PulseAudio Device Chooser* utility from *Synaptic*. When you run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

From there you will be able to select the default card for input and output. In the *Output Devices* tab you should see your USB headset listed. Just right-click on it and enable the *Default* option to set it as the default output device, if you want.

If after doing the above you are not getting audio from *Flash* through your USB headset, or if you don't want to set your USB headset as the default output device but only to use it for *Flash*, then the thing you need to do is, first of all, to put a *Flash* video *playing* in Firefox. Then open the *PulseAudio* volume control again and select the *Playback* tab.

There you should see the audio stream of the *Flash* video listed. Right-click on it and select *Move Stream...* and in the list that will appear select your USB Headset. *PulseAudio* should remember your choice from now on.

For this to work you'll need to set your sound playbacks (i.e. for Sound Events, Music and Movies, as you said) in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*. You can do the same for your inputs, set them to *Autodetect*, if you have specified an input device in the *PulseAudio Device Chooser*, for example your ATI sound card.

Hope that helps.

Thanks for typing all of that into this thread.   I had the same problem.  Reading and adapting your directions for my system got flash audio working.

Thanks much

---

### Post by Lil Jimmy on 2009-05-03
> **kostkon said:**
> OK. Then You need to install the *PulseAudio Device Chooser* utility from *Synaptic*. When you run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

From there you will be able to select the default card for input and output. In the *Output Devices* tab you should see your USB headset listed. Just right-click on it and enable the *Default* option to set it as the default output device, if you want.

If after doing the above you are not getting audio from *Flash* through your USB headset, or if you don't want to set your USB headset as the default output device but only to use it for *Flash*, then the thing you need to do is, first of all, to put a *Flash* video *playing* in Firefox. Then open the *PulseAudio* volume control again and select the *Playback* tab.

There you should see the audio stream of the *Flash* video listed. Right-click on it and select *Move Stream...* and in the list that will appear select your USB Headset. *PulseAudio* should remember your choice from now on.

For this to work you'll need to set your sound playbacks (i.e. for Sound Events, Music and Movies, as you said) in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*. You can do the same for your inputs, set them to *Autodetect*, if you have specified an input device in the *PulseAudio Device Chooser*, for example your ATI sound card.

Hope that helps.

Thanks! The 2nd thing worked. I didn't change the sound playbacks to autodetect, though, but yeah :P thanks!

---

### Post by tomsyco on 2009-05-08
I'm having the same problem. Have only one audio card and i have reinstalled flash.

---

### Post by b05q on 2009-05-09
Thanks, I've had trouble w/my inspiron 9300, but that fixed it.

---

### Post by goatroapr on 2009-05-17
Yeah, the solution from kostkon fixed it. Easier than I was making it out to be. Many thanks

---

### Post by mechaxl on 2009-08-21
> **kostkon said:**
> OK. Then You need to install the *PulseAudio Device Chooser* utility from *Synaptic*. When you run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

From there you will be able to select the default card for input and output. In the *Output Devices* tab you should see your USB headset listed. Just right-click on it and enable the *Default* option to set it as the default output device, if you want.

If after doing the above you are not getting audio from *Flash* through your USB headset, or if you don't want to set your USB headset as the default output device but only to use it for *Flash*, then the thing you need to do is, first of all, to put a *Flash* video *playing* in Firefox. Then open the *PulseAudio* volume control again and select the *Playback* tab.

There you should see the audio stream of the *Flash* video listed. Right-click on it and select *Move Stream...* and in the list that will appear select your USB Headset. *PulseAudio* should remember your choice from now on.

For this to work you'll need to set your sound playbacks (i.e. for Sound Events, Music and Movies, as you said) in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*. You can do the same for your inputs, set them to *Autodetect*, if you have specified an input device in the *PulseAudio Device Chooser*, for example your ATI sound card.

Hope that helps.

Thanks a ton! Choosing the stream for my firefox flash plugin fixed my problem with no sound.

---

### Post by spikoley on 2009-08-23
> **kostkon said:**
> OK. Then You need to install the *PulseAudio Device Chooser* utility from *Synaptic*. When you run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

From there you will be able to select the default card for input and output. In the *Output Devices* tab you should see your USB headset listed. Just right-click on it and enable the *Default* option to set it as the default output device, if you want.

If after doing the above you are not getting audio from *Flash* through your USB headset, or if you don't want to set your USB headset as the default output device but only to use it for *Flash*, then the thing you need to do is, first of all, to put a *Flash* video *playing* in Firefox. Then open the *PulseAudio* volume control again and select the *Playback* tab.

There you should see the audio stream of the *Flash* video listed. Right-click on it and select *Move Stream...* and in the list that will appear select your USB Headset. *PulseAudio* should remember your choice from now on.

For this to work you'll need to set your sound playbacks (i.e. for Sound Events, Music and Movies, as you said) in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*. You can do the same for your inputs, set them to *Autodetect*, if you have specified an input device in the *PulseAudio Device Chooser*, for example your ATI sound card.

Hope that helps.

Thanks, it worked after selecting Move Stream.  But now Totem does not play sound.  Any ideas?

Update:  I got it working!!!  I had to have Totem open and then the option for PulseAudio Device Chooser showed up and I could select the playback device.

---

### Post by The-Don on 2009-10-25
Thanks kostkon, it worked for me after all the other attempts.

---

### Post by Matt P on 2009-11-19
> **kostkon said:**
> OK. Then You need to install the *PulseAudio Device Chooser* utility from *Synaptic*. When you run it (it will have a menu entry in *Applications &#8594; Sound & Video*), left-click on its icon in the system tray and select *Volume Control*.

From there you will be able to select the default card for input and output. In the *Output Devices* tab you should see your USB headset listed. Just right-click on it and enable the *Default* option to set it as the default output device, if you want.

If after doing the above you are not getting audio from *Flash* through your USB headset, or if you don't want to set your USB headset as the default output device but only to use it for *Flash*, then the thing you need to do is, first of all, to put a *Flash* video *playing* in Firefox. Then open the *PulseAudio* volume control again and select the *Playback* tab.

There you should see the audio stream of the *Flash* video listed. Right-click on it and select *Move Stream...* and in the list that will appear select your USB Headset. *PulseAudio* should remember your choice from now on.

For this to work you'll need to set your sound playbacks (i.e. for Sound Events, Music and Movies, as you said) in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*. You can do the same for your inputs, set them to *Autodetect*, if you have specified an input device in the *PulseAudio Device Chooser*, for example your ATI sound card.

Hope that helps.


Yes! Thank you so much for this

---

