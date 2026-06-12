---
title: "Dimension E520 - No sound card device listed?"
date: 2008-02-01
forum: Dell  Ubuntu Support
---

### Post by jtp51 on 2008-02-01
I have a Dimension E520 running Ubuntu 7.10.
 
When I test my sound under the System->Prefs->Sound dialog - it gives me this error for each "Test" button:
 
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

After receiving that error, I found that I have no sound card device listed in the Sound dialog pick list?
 
I only have the onboard soundcard that came with the E520 and I tried to switch between Alsa and OSS with no luck there either.
 
I tried the command with no results:
 
sudo chmod a+rwx /dev/dsp

And I've searched this forum with no successful results.
 
I'd appreicate any help with this.
 
Thanks,

---

### Post by linuxwizard on 2008-02-03
Go through this

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

