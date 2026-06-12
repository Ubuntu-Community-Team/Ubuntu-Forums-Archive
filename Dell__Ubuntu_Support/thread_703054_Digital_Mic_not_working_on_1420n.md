---
title: "Digital Mic not working on 1420n"
date: 2008-02-20
forum: Dell  Ubuntu Support
---

### Post by oryan_dunn on 2008-02-20
I've got the custom Dell l-b-m module installed, along with the digital mic set to digital mic 1 in the options.  The gnome sound preferences give the very common "Failed to construct test pipeline" error.  Sound recorder is set to digital, but no sound is recorded.  Is there anyway I can test this to see if my mic is actually working?  I want to be sure that the problem is with software and not my hardware.  If it is hardware related, then I'd like to know now instead of after my laptop is out of warranty.

---

### Post by notwen on 2008-02-21
It looks as if you've done exactly what Dell's Linux wiki recommends for [this issue]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work").  Have you rebooted by chance?  I also have a Inspiron 1420n and I was able to get my mic working just fine w/o any issue.

As far as recording goes you're on your own.  Do you use Skype, you could use it to test your mic.  Best fo luck figuring out this issue. =]

---

### Post by oryan_dunn on 2008-02-21
> **notwen said:**
> It looks as if you've done exactly what Dell's Linux wiki recommends for [this issue]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work").  Have you rebooted by chance?  I also have a Inspiron 1420n and I was able to get my mic working just fine w/o any issue.

As far as recording goes you're on your own.  Do you use Skype, you could use it to test your mic.  Best fo luck figuring out this issue. =]

Just out of curiosity, if you do a search in synaptics for backports, what title does the LBM come up with?  Also, does your mic work with Ekiga, Sound Recorder?  I know it probably doesn't work with the Gnome sound preferences.  I wonder if my problem is actual hardware.  Do you know of any tools that would give a command line output of input levels of the mic?

---

### Post by oryan_dunn on 2008-02-23
So far, the only way I know that I can test if the mic actually works is to try to install windows in the computer and see if it works there.  Does anyone have a more sane idea?

---

### Post by notwen on 2008-02-24
I'm clueless other than searching Synaptic for other applications that may use a mic.  Wish I could be of more assistance, but that's all I have to offer. =\

---

### Post by oryan_dunn on 2008-02-24
Well, I tried a suggestion elsewhere and booted Hardy alpha.  I was able to make a recording from there (the sound output didn't work), but then was able to play it back in Gusty.  So, I have confirmed that the hardware works, but there is some error in the software preventing the mic from working.

---

