---
title: "volume control"
date: 2007-10-26
forum: Desktop Environments
---

### Post by higashi on 2007-10-26
Okay, i'm not sure where i should be posting this, but this seemed like the most appropriate place. I don't know why i haven't asked this before, but ever since i first got ubuntu, i've been having this problem with my volume control. Whenever i would click my volume control thing, it gives me the liittle volume slide, but it doesn't work.. to change my volume i have to double click on my little volume button and wait for the window to open, and then i have to adjust my headphone and my PCM volume.  Anyone know how to fix that??

---

### Post by Dave Curry on 2007-10-27
I have the same deal with my Inspiron 9300. I have to slide my "master" and "pcm" controls. I would like my volume to be hooked to my laptop's volume button.

---

### Post by iain010100 on 2007-10-27
I'm not clear on the description of the problem, maybe it's the same as mine? My keyboard has volume control buttons. When I use them, a speaker icon appears on the screen and reacts to the buttons I press (full to mute), but the actual volume output doesn't change, and neither does the volume icon in the panel.

---

### Post by higashi on 2007-10-27
what i mean is that my master volume control doesn't affect my volume whatsoever.. to change the volume, i have to adjust the headphones volume and pcm volume..

---

### Post by JPJ007 on 2007-10-27
I have a similar problem.  The volume buttons on my laptop control Master Volume, which works fine for my laptop's internal speakers.  However, this doesn't affect the volume of headphones or external speakers at all.  I suppose the ideal solution would be a way to make Master volume control both.  Anyone have any suggestions?  I have just a couple of day's experience with Linux (loving it so far) so I have no clue.

---

### Post by higashi on 2007-10-28
hah, cool. Have fun with your new linux :)

---

### Post by wonder76 on 2007-11-10
it's easy

master controls internal frontal speakers,master mono controls the subwoofer,headphone controls volume when there is something connected to lineout (headphones,external speakers)

with right click on volume control icon in traybar (preferences), it's possible to link some volume controls with the applet volume control

in system/preferences/audio it's possible to link these volume controls to the volume controlled by multimedia buttons


sorry for my poor english....:(

---

### Post by mcduck on 2007-11-10
Just go to System/Preferences/Sound, and in the bottom of the Devices-tab there is asection where you can select which device and mixer track(s) the volume applet and your multimedia keys control. If you hold the Ctrl key you can select multiple tracks at the same time.

---

### Post by MikeyXX on 2007-12-21
You'll want to bind Master and PCM.

However, I think it still causes the sub to remain.

I ended up going to System->preferences->sound and choosing the ALSA for all my playbacks, then going down and hitting ctrl and selecting everything from Master down to PCM. Seems to work better for me. However, the mute doesn't completely mute it.

---

