---
title: "No sound after upgrade to Hardy"
date: 2008-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by inca99 on 2008-05-24
Hello all, I have just purchased a Dell Inspiron 1525N which came preloaded with Gutsy. I used the update manager to upgrade to Hardy and since then I have no sound. I have followed the advice on (Ubuntu 8.04/Issues/No Sound After Distribution Upgrade - [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)) but this has not helped. I'm a complete noob on ubuntu so any help gratefully received, thanks.

---

### Post by inca99 on 2008-05-24
I read on another forum it can be down to the kernel, on boot I went into the GRUB menu and selected 2.6.24-14 (my default was 2.6.24-17). Now I have sound!?

---

### Post by AWDriver on 2008-05-25
Take a look at [http://ubuntuforums.org/showthread.php?t=803956]("http://ubuntuforums.org/showthread.php?t=803956")

From my experience on an XPS 1330M:

Open the mixer, max all the playback levels (master, PCM, front, etc).  Tell it to show surround and the different channels in preferences (think that's where you pick it, don't have it in front of me, typing this from Vista).
Click select device, change between them and ensure the playback devices are all maxed.  This should be the case if you maximized them from the first step.

What you will need to do to control sound levels is use the PCM slider, not the master slider.  The master slider needs to remain 100%.  Right click the audio icon in the toolbar and select preferences.  Change the device to PCM and select the only option below it.  This will make the slider control the volume slider you need it to.

To have keyboard shortcuts control it instead of master, go to the "control panel"/select sound out of the system menu.  The last option in that sound control panel allows you to select what keyboard buttons will control.  Again, choose PCM.

---

### Post by jlodowica on 2008-05-26
No sound on DELL XPS M2010

Help please

James

---

### Post by persev on 2008-06-04
The volume control did not find any elements and/or devices to control.This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

---

### Post by thorcik on 2008-06-05
in my case it was enough to install complete generic kernel (the canonical one, package linux-image-generic), the dell modules rendered my wireless card (intel 4965) unable to connect to any network.
I have m1330.

---

