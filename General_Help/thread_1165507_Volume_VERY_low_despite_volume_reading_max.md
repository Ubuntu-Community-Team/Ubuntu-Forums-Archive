---
title: "Volume VERY low despite volume reading max"
date: 2009-05-20
forum: General Help
---

### Post by cody7002002 on 2009-05-20
My volume is shown to be turned all the way up on the volume control but the volume on anything is still very low. I was running windows xp before installing NBR and the volume was much louder.



P.S. I've been having a lot of problems with NBR X( this is the third or fourth thread i've made concerning problems i'm having with it.

---

### Post by paradigm2 on 2009-05-20
Install gnome-alsamixer either from synaptic or from a terminal

```

sudo apt-get install gnome-alsamixer

```

Adjust volume settings accordingly.  Particularly pay attention to PCM which sometimes is set low.

If the problem persists let us know which sound card you have

```

lspci

```

---

### Post by cody7002002 on 2009-05-20
I downloaded the mixer and it was already all the way up. 

and if i'm looking at the right thing it says my audio device is Intel corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by paradigm2 on 2009-05-20
> **cody7002002 said:**
> I downloaded the mixer and it was already all the way up. 

and if i'm looking at the right thing it says my audio device is Intel corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Maybe play with the alsa mixer (Applications -> Sound and Video -> Gnome Alsa Mixer) a bit with the different settings.  Don't be afraid.  Especially look at things like Front, center, PCM, Master, Mono....

If that doesn't work there have been some issues with Intel HDA devices.  Often success isfound by updating the alsa and pulseaudio version to an unofficial newer release:

eneral instructions (for Jaunty) to upgrade to an unofficial version of alsa and pulseaudio (use only if willing and no one else can help) :

To install a much newer alsa and pulse audio (again this is unofficial) :

1. Add these unofficial PPA's to your sources list or else the "Third Party Repositories" in Synaptic Package Manager.

deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main

2. Upgrade all the upgrades suggested from the repository.. (run update manager) ... then reboot.

**Note: I would not try the above until nothing else works**

Failing this, on my laptop I found going to the (unofficial) 2.6.30rc6 kernel helped as there have been some fixes to intel hda.  But doing this is highly unofficial and comes with risks.  Last resort only (which is why I have not put up any instructions for doing this yet)

---

### Post by cody7002002 on 2009-05-20
When I go into alsamixer the tab says realtek ALC269 what does that mean? and I don't see any settings like you have described, the only things displayed are PCM LineOut Capture. Then iSpeaker at the bottom with a checked checkbox

---

### Post by cody7002002 on 2009-05-20
I FIXED IT! I just turned up the lineout volume all the way up and it's perfectly loud now =) thanks for your help!

---

