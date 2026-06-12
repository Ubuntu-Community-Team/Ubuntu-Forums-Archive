---
title: "Capture from mic array on m1330 is extremely low volume"
date: 2009-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Declination on 2009-05-14
That pretty much sums everything up. I have a Dell M1330 running 9.04. Everything works fine except for audio capture from the microphone array. It is extremely quite, to the point where I thought it was muted. The only reason I know it isn't is because I can see the input volume bar move a little bit when using the Sound Recorder if I put my hand right next to the array (like 2 inches) and snap.
What could be wrong?

---

### Post by Lemmy The Koopa on 2009-05-14
Did you try this?

Right click on volume
Click "Open Volume Control"
Click "Preferences"
Check all of the boxes that say "Recording"
Raise the volume of the new options all the way up
Try recording again
Turn down the volume to suit your needs.

If not, I can't help you.

---

### Post by Declination on 2009-05-14
No change.

---

### Post by Declination on 2009-05-15
So, potentially more information that might be useful in the attached picture. Here is an example of what Pulseaudio's volume control says my input volume is at. The source of sound (me) is equidistant from the two microphones, yet for some reason the built-in microphone gets almost no volume. Next to it is a picture of my volume controls. The microphone options in the mixer (with what looks like the muted icon) will not stay unmuted. Whenever I try the next time I open the preference panel they are muted again.

---

### Post by tacantara on 2009-05-15
Declination:  Been there a few times myself with the mic problems.  Two things that have worked for me are shown in the following threads that I've started on this issue in the past few months:  [http://ubuntuforums.org/showthread.php?t=1073884](http://ubuntuforums.org/showthread.php?t=1073884) is the first time I experienced mic problems, and [http://ubuntuforums.org/showthread.php?t=1153117](http://ubuntuforums.org/showthread.php?t=1153117) is a more recent problem that occurred after I did a reinstall of Ubuntu for Dell.
 
Either one of these fixes should do the trick.  Let me know how you make out with this.  Good luck :)

---

### Post by Declination on 2009-05-16
That didn't appear to help. I am particularly interested in the +20dB boost option though. I can't seem to find it, or anything similar. Since I know I actually have sound recording capability, I feel like that would fix the problem. Anyone else running 9.04 on an M1330 know where this option is?

---

### Post by Declination on 2009-05-17
Problem solved (I think).
So, what I had to do was. 

[LIST=1]
[*]Install pulse audio device chooser
[*]Run pulse audio device chooser
[*]Select the manager option from the panel applet
[*]Select the devices tab
[*]Select the device alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 which was HDA Intel
[*]Click properties
[*]Increase volume to ~140%
[/LIST]
And all is well.

---

### Post by ejnowak on 2009-09-18
I had similar (or identical?) problem.  I executed the old 'sudo apt-get remove pulseaudio'.  Did not fix.  I then installed gamix from the ubuntu repository, and ran it (Applications>Sound and Video>ALSA Mixer)  to set up mic input, with 'front mic' as the input setting, selecting every input option and setting to max volume, and selecting ALSA for my audio settings in System>Audio.  In Skype selected 'Default Audio' for all of the sound options.  Finally have good microphone audio level on Skype!  Tried many other posted suggestions without success.  Running 32bit Ubuntu 9.04 on M1330, external mic.  Hope this works for at least some folks with similar problem.

---

### Post by nwadams on 2009-09-19
hi all.

I have an xps m1330 running 9.04 and I have everything working properly. What i did was I installed gnome-volume-control-pulse, removed the sound applet (when you log out and log in again the new pulse audio one will show up. You will have two sound preferences in your system-->preferences menu. one of them is the new pulse audio one where you can modify the mic volume more. The other, I made look like the attached screenshot.

May I ask what program you are trying to use your mic for?

nwadams

---

