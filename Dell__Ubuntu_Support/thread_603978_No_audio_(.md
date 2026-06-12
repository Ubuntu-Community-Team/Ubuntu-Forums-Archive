---
title: "No audio :("
date: 2007-11-05
forum: Dell  Ubuntu Support
---

### Post by tyraeon on 2007-11-05
I don't understand what's going on...I have a Dell XPS M1710 laptop, new condition. Got it in August.

All of a sudden, starting yesterday, no audio works on it. The laptop speakers won't play anything, and my speakers won't play anything if they're plugged in. I've toyed with all the volume knobs, there's even an external volume adjuster on the computer itself. Nothing works.

Weird thing is that audio works in Windows (I dual boot).

Anyone ever encountered this?

---

### Post by StefAndrew on 2007-11-05
I'm having a similar problem, but my sound has never worked.  I guess Ubuntu doesn't recognize the sound on my Vostro 1500.  I dual boot and it works fine in Windows.  I haven't had any luck with getting the sound working either.

---

### Post by Skuzniak on 2007-11-05
StefAndrew, these steps should clear up your sound problem. I have a Vostro 1400, and it made sound work perfectly for me. I'm assuming that the 1400 and 1500 share the Sigmatel Audio chip:

sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.



Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot and see if sound works.

tyraeon, these steps may fix your sound problem. Can you give us more detail about the problem? Does the hardware information application show a soundcard installed? Did the sound turn off when you came back from suspend or hibernate? Are you sure your speakers are not muted through the sound interface?

---

### Post by StefAndrew on 2007-11-05
Cool, thanks.  Will have to try that when I get home, I can't find my install CD and I'm at work and can't use my laptop here, at least not with internet.  =/

Thanks again.  I will let you know how it turns out.

---

### Post by tyraeon on 2007-11-06
I tried those commands, didn't fix the problem.

Thanks for the input, though. Anyone else have an idea?

---

### Post by StefAndrew on 2007-11-06
I tried the commands as well, to no avail...  No error messages, but still no sound devices showing as installed.

---

### Post by Skuzniak on 2007-11-06
No sound devices showing as installed is a different problem than what I had. What I gave you would have fixed a potential driver issue, not a not-recognizing issue.

One last thing you might want to try is change the "options snd-hda-intel model=5stack" line to "options snd-hda-intel model=3stack"

I had it as 3 stack when my sound first worked. At 3 stack, sound would still dissapear when I suspended/returned ubuntu, but a change to 5 and the alsa steps I listed fixed it for me. Maybe it needs to be done in that order? I'm no expert, but perhaps it's possible.

Sorry I couldn't be more help. :(

---

### Post by cattleeyes on 2007-11-10
Same thing happening here on my old Dell Dimension!
Everything seems to be in its place, there are no error messages, everything is checked the way I had them selected before the update, and yet no audio!

---

### Post by tyraeon on 2007-11-13
My hardware information shows ALSA Sequencer and ALSA Timer. Both of these register as "Sound."

Also, I installed a drum machine program called Hydrogen. The first runtime error it gave me was: [ERROR]     AlsaAudioDriver     [alsaAudioDriver_processCaller] XRUN

Perhaps this helps?

---

### Post by Skuzniak on 2007-11-13
Hi again guys,

tyraeon, it still seems to me like there is a driver issue going on, I get that feeling from the error message. Since the hardware manager isn't being very helpful with a soundcard name, when you boot into windows could you write it down for us? That would help us loads. One thing to try before you boot into windows is remove the line from alsa-base I asked you to add before. I'm fairly sure that line is only going to affect the soundcards in Vostro's and Inspirons, I think the XPS line uses a different type of card.



StefAndrew, try changing the line I asked you to add in alsa-base to the following:

options snd-hda-intel probe_mask=1 model=3stack

or

options snd-hda-intel probe_mask=1 model=5stack

---

### Post by jdelaros1 on 2007-11-13
Have you tried installing linux-backports-modules?

See [https://bugs.launchpad.net/dell/+bug/131133](https://bugs.launchpad.net/dell/+bug/131133)

---

