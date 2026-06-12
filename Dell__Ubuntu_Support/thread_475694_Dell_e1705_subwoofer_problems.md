---
title: "Dell e1705 subwoofer problems"
date: 2007-06-16
forum: Dell  Ubuntu Support
---

### Post by helixed on 2007-06-16
Hey everybody,

I know my laptop isn't one of the Dells to ship with Ubuntu preinstalled, but I thought somebody may be able to help me out on this forum anyway.  I was able to get my subwoofer working using the guide [here]("http://ubuntuforums.org/showthread.php?t=270739&highlight=helixed&page=2"), but the subwoofer is not linked to the master volume control, so when I try to readjust the master volume using the multimedia keys on the front it only adjusts the two stereo speakers.  Does anybody know how I can link the subwoofer to the master volume control?

Thank you,

Helixed

---

### Post by helixed on 2007-06-17
Can anybody help me?

Thanks,

Helixed

---

### Post by eightdollarbeer on 2007-06-20
heres what you do. goto the mixer enable the lfe and master set them both to max or whereever you like the sound i blast them out . then close it up left click on the volume control if not open run kmix or similar choose select master channel then select pcm . now your lfe and master stay set and pcm controlls your volume. future audio mixer fixes this . hope this is what you wanted

---

### Post by helixed on 2007-06-23
Not quite.  I need the volume manager to coltrol both the pcm and the lfe.  Having them stay put is kind of where I'm at right now.  

Thanks for the reply though,

Helixed

---

### Post by James.Dedon on 2007-06-24
I was having the same problem as you.  I couldn't turn down the volume of my subwoofer.  So I cheated and now just use external speakers, thus disableing the subwoofer and the onboard speakers.

---

### Post by Tethtibis on 2007-06-26
if the sub has a "stereo" jack, try attatching it to input monitor, "yellow" or any other open port on your audio card, then try messing with the different volume levels whn you double click the volume icon.

---

### Post by cianclarke on 2007-06-28
> **eightdollarbeer said:**
> heres what you do. goto the mixer enable the lfe and master set them both to max or whereever you like the sound i blast them out . then close it up left click on the volume control if not open run kmix or similar choose select master channel then select pcm . now your lfe and master stay set and pcm controlls your volume. future audio mixer fixes this . hope this is what you wanted

Having done some searching, this worked a treat. Sorry to bump - just hoping google might pick up on this thread a bit better. 
Cian

---

### Post by fmaste on 2007-06-30
My sub woofer is working out of the box with Feisty. But I have the same problem with the multimedia keys, I fix it doing this:

Double click on the volume control near the clock and make sure you have Alsa device selected. (File -> Change device -> HDA Intel (Alsa mixer) )
Leave your sub woofer on and at full volume.

Now go to System -> Preferences -> Sound
If you look carefully on the lowest part of the window it says "Select the device and track to control with the keyboard....". Simple, where it says "Default mixer tracks" select "HDA Intel..." as the device, them PCM instead of Master or you can select both Master and LFE.
Choose the one that best fits your needs.

Hope it works

---

### Post by helixed on 2007-06-30
Awesome, this worked out perfectly.  Thanks everybody.

Helixed

---

### Post by Basher52 on 2008-04-21
Man, this is why I love the linux community. Solutions for everything and almost every problem has a solution. <3 Ubuntu

---

### Post by camino262 on 2008-04-22
Thanks, worked great on my dell XPS M1710.

---

### Post by stevenmansour on 2008-06-12
Thanks a million, couldn't find how to sync my subwoofer and speakers on my Dell M90 - switched back to ALSA after Pulse Audio kept causing problems.

---

