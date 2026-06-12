---
title: "[SOLVED] XPS M1330 Linux Backports from Dell = BROKEN"
date: 2008-03-27
forum: Dell  Ubuntu Support
---

### Post by AegisTalons on 2008-03-27
Hey guys,
So I'm already frustrated with Microsoft because Vista thinks is God's software to humans. Just in case you don't know, be careful in deleting the Vista partition because it will delete your MBR. I learned that the hard way. Also some screwy thing happened where my partition table was also deleted, so I had to reformat and reinstall my entire OS (XP + Ubuntu).

Now on to Dell. The XPS M1330 is a pretty solid laptop hardware wise. Its in the software where Dell is lacking. So if you check out Dell's own [wiki]("http://linux.dell.com/wiki/index.php/Wiki_Main_Page") about Linux you can see. So I wanted to have the built in microphones working. So I decided that the backports would work. I downloaded and forced them to install (they are i386, and I run amd64). Well it completely screwed up my sound as in the computer can only do system beeps now. Let me just tell you that's not the most pleasant sound there is.

Does anyone know first how to remove these so called backports and second how to get the mic working? Thanks for your help.

---

### Post by notwen on 2008-03-27
I cannot help you w/ the backports packages you installed.  I can however help you w/ your mic.  you wer eon the right track by going to Dell's Linux Wiki, but if you would have dug a little deeper you woudl have came across [this]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work").  Dell has a done a nice job posting any bugs/issues and then providing a fairly easy fix/workaround for said issue on each individual model.  Post back if you have any issues.  =]

---

### Post by AegisTalons on 2008-03-27
See the thing is I did use that post. And the deb included in that wiki is the backports I'm referring to. Have you installed those backports in the deb? What happens is that it broke my system. No sound just system beeps.

---

### Post by sdennie on 2008-03-27
Forcing the installation of the backports deb was a bad idea.  It contains kernel modules that are only compatible with the version and architecture it specifies in the name of the deb file so, it clobbered your kernel/arch specific modules with incompatible things.  Dell doesn't have an amd64 version because they don't ship amd64 machines.

To at least get your sound back to a usable state (I don't use my mic so I don't know if it will fix your mic problem), you can download the latest version of the also drivers ([ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)), build and install it.  It's fairly straightforward but, if you aren't familiar with kernel modules, you'll like have to reboot after you've installed the new drivers.

---

### Post by AegisTalons on 2008-03-27
So I removed the package from Dell and I got my sound back to the original state it was in: working but no mic. Does anyone know how to get the mic working?

---

### Post by sdennie on 2008-03-27
I just tried out the mic (using the alsa 1.0.16 drivers I mentioned above) and, I was able to get it working by turning on "Digital" and "Digital Input Source" in the sound preferences that I get from double clicking the sound icon on the panel.  An "Options" panel appeared and I selected "Digital Mic" for "Digital Input Source".  After that, I was able to record sound in the Sound Recorder tool if I tell it to record from "Digital" but, I haven't tried any other apps.  This was all on an XPS m1330.  Hope that helps.

---

### Post by AegisTalons on 2008-03-29
So I tried installing the ALSA Drivers from source, and I broke it. Steps I did:
Download the source file from your link.
Extracted to Desktop.
Under terminal, cd into extracted folder
ran "./configure"
ran "make"
ran "sudo make install"
Restarted the system. I don't have sound anymore please help.

---

### Post by sdennie on 2008-03-29
I think the useful mixer settings have changed with 1.0.16 for the card in the m1330.  You may want to check if enabling some more of the volume controls in the Volume Applet helps.  Master and PCM are the ones that work for me.  It's possible that they are currently muted for you.

That's assuming the drivers are properly loaded.  You may want to do a:
```

lsmod | grep snd_hda_intel

```

And, if you get output, the drivers should be loaded.

---

### Post by AegisTalons on 2008-03-29
The drivers are not loaded. When I double click on the Volume Applet, I get the following error: "No volume control GStreamer plugins and/or devices found." Same error I got when I tried Dell's drivers suggesting that either I didn't compile it correctly or I'm not loading them correctly.

---

### Post by AegisTalons on 2008-03-30
Looks like I finally got it. Took a while but I took a look at [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and [this]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt").

For the second one, search for snd-hda-intel and you'll see some helpful stuff. I found that the first link was very helpful. Thanks for everyones help.

The mic is working along with everything else on the sytem.

---

### Post by sdennie on 2008-03-30
Glad to hear that everything is working.  Enjoy the great machine.  ;)

---

