---
title: "Sound?"
date: 2009-02-22
forum: General Help
---

### Post by Aramed on 2009-02-22
Ok well here's what happened. I installed ubuntu onto a My Book 3-4 months ago. I've been booting from USB ever since because I wanted to keep Windows XP installed on the Computer itself. However, one day a week or so ago I started it up like any other time and then I realised that the sound wasn't working at all. I checked to make sure the speakers were on and plugged in properly and they were. Any ideas on what could have made them stop working?

---

### Post by jpeddicord on 2009-02-22
I find some weird times when my sound goes out because the volume controls reset to zero. Couldn't explain why, but open a terminal (Applications > Accessories > Terminal) and type `alsamixer` to open your full set of volume controls. Try adjusting those sliders using the arrow keys and see if it helps.

If that doesn't work, there might be a hardware support or driver issue. Paste the output of `lspci -vvvnn` in a terminal here so we can see the full details of your sound card. :)

---

### Post by Aramed on 2009-02-22
I looked at the volume controls and they were fine. Since I don't know how to put the specs in a terminal on here. I Saved the specs of my sound card to a .odt file and attached it.

---

### Post by Aramed on 2009-02-24
I'm aware people here frown upon double posts but. I just tried typing pulse audio into the terminal and this is what I got as a message. Could this be the reason my sound stopped working?

> jacob@UbuntuBook:~$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.


---

### Post by slowth5 on 2009-02-24
Hi Aramed, I have no sound, and I also receive the same error as you posted.  I tried a clean install of 8.10, and the sound works initially, but I lose sound when I update the system.  I've tried troubleshooting, but to no avail.

---

### Post by Aramed on 2009-02-24
I might try to remove and then reinstall pulseaudio. Anyone have a walkthorugh I could use? Or if it's even worth the time to do that instead of backing up all my files and then reinstalling Ubuntu.

---

### Post by slowth5 on 2009-02-24
This thread has instructions for reinstalling pulseaudio:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


You can also try this one:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


Well, I went back through the first guide, and wouldn't you know I found a solution.  It was this little line:

> Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.


That has always been checked and it's never caused a problem.  I'll put it on my problem list now.

Keep me updated Aramed, I'll do my best to help.

---

### Post by zeroemissions on 2009-02-25
Have you made sure the master channel is unmuted in alsamixer?? If it has a 'MM' at the bottom of the slider then it is muted. Select that channel and hit 'M' to unmute. (it should change to a '00' when unmuted) I find with mine the volume has to be at full to work at all.

---

### Post by Aramed on 2009-02-25
Thank you Slowth5 for the links I'll try it out when i get home today.

> **zeroemissions said:**
> Have you made sure the master channel is unmuted in alsamixer?? If it has a 'MM' at the bottom of the slider then it is muted. Select that channel and hit 'M' to unmute. (it should change to a '00' when unmuted) I find with mine the volume has to be at full to work at all.

Alsamixer did not ever get muted.

---------------
Edit:

Good news I have sound again bad news I can't use the buttons on the keyboard to adjust the volume any more. But I can figure that out later. So here's what I did. 

While going through the first link that Slowth5 shared with us. I read something about trying a new user account. While on the screen for creating users. ( System > Administration > Users and Groups ) I looked under my current accounts settings and noticed under the "User Privileges" tab that "Use audio devices" was not checked. So I checked it then restarted and it was working again.

---

### Post by slowth5 on 2009-02-25
Glad your sound is restored.  I found a couple of posts that might help the keyboard volume issue.

> **gbrethen said:**
> I solved my problem by changing the Device Mixer in the sound settings.  I also Changed from ALSA to PulseAudio Sound Server.  After doing that, now my volume and mute keys work.

> **prkos said:**
> You have to have the keyboard shortcuts setup under System > Preferences > Keyboard shorctuts to get a reaction on screen when pressing the keys, and for the no impact problem look for a solution here [http://ubuntuforums.org/showthread.php?p=6689951](http://ubuntuforums.org/showthread.php?p=6689951)

---

### Post by Aramed on 2009-03-06
> **slowth5 said:**
> Glad your sound is restored.  I found a couple of posts that might help the keyboard volume issue.

Sorry it took so long to get back to you. But both of the keyboard buttons were set and hey respond with the volume adjustment bar that appears on the screen. Is there a way that you could change the amount the volume goes up and down with each press? It seems that it's working however the response to loudness is just little to none.

---

