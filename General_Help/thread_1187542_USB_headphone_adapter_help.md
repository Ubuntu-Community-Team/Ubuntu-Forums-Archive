---
title: "USB headphone adapter help"
date: 2009-06-14
forum: General Help
---

### Post by recharge330 on 2009-06-14
I've never had linux before and I just installed ubuntu but I can't get the sound working. I have a AC'97 sound card wich seems to have a lot of problems so I thought I should try a usb adapter. I looked around and a lot of people were suggesting using "sudo gedit /etc/modprobe.d/alsa-base" and then changing the 2 in "options snd-usb-audio index=-2" to a 1. That command just brings me to a blank file but if I go to the folder it's in there is a .conf with the "options snd-usb-audio index=-2" line. I think I may have accidentally changed the alsa-base file in the terminal. If I try to edit that or the blank file it says "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." If I move the blank file out of the folder I can edit it then move it back. If someone could tell me what file to change and how to do it I might be able to get this to work.

---

### Post by kostkon on 2009-06-14
What version of Ubuntu do you have?

---

### Post by recharge330 on 2009-06-14
9.04

---

### Post by kostkon on 2009-06-14
OK. Then, the suggestions you were given are more or less wrong, or let's say not the best suitable ones.

Nevertheless, the thing you need to do is to install the *PulseAudio Device Chooser* utility using *Synaptic*.

Then you need to run it and it will put its icon in your system tray. Left-click on it and select *Volume Control*.

Select the *Output Devices* tab and you should see your USB adapter listed there. Right-click on its entry and enable the *Default* option to make it the default output device in your system.

Some applications (very very few of them, e.g. *Flash*) may need to manually send their audio stream from your onboard card to your USB adapter. Don't worry you only need to do this once.

In the case of Flash sending its audio to your onboard and not to your adapter, just open the *PulseAudio* volume control again and select the *Playback* tab. You should see there the audio stream of the *Flash* you are playing. Right-click on it and select *Move Stream...* and in the list that will appear select your adapter.

You can set *PulseAudio Device Chooser* to start every time you login from its preferences, if you want.

For more info regarding the above, check [this very useful thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

Hope that helps.

---

### Post by recharge330 on 2009-06-14
Thank you!!!! It worked great. I couldn't find the program at first but I just had to app-get padevchooser.

---

### Post by kostkon on 2009-06-14
> **recharge330 said:**
> Thank you!!!! It worked great.
:)
> **recharge330 said:**
> I couldn't find the program at first but I just had to app-get padevchooser.
Yes, I assume that you used the quick-search in *Synaptic*. The problem is that it does not work in all cases, thus it is better to always use the full search option. It's the button next to the quick-search input field ;)

---

