---
title: "ALSA headphone problems"
date: 2006-08-18
forum: Desktop Environments
---

### Post by fieldstone on 2006-08-18
I've posted about this before but didn't get any responses, so thought I'd try it again.

I've recently set up Dapper Drake AMD64 on my new Compaq Presario V3010US laptop, and I've got pretty much everything working but my headphones. I plug them in and they just don't work. I'm using the ALSA driver (in the mixer it shows up as "HDA NVidia"), but there doesn't seem to be any setting I can change to get my headphone jack working. (Installing the nForce audio driver didn't change anything, so I got rid of it; compiling and installing the ALSA drivers myself also didn't work, although I'm pretty sure I did it wrong.)

LSPCI gives me the following about my sound controller:

0403: nVidia Corporation MCP51 High Definition Audio (rev a2)

Could someone please help me enable the headphone output on this controller?

---

### Post by kb3hkg on 2006-08-18
Go into alsamixer by command line. Make sure nothing is muted, I found that with my laptop the headphone jack is actually PC Speakers in alsamixer and I changed that to get it to work. It is possible your problem is similar.

---

### Post by fieldstone on 2006-08-18
> **kb3hkg said:**
> Go into alsamixer by command line. Make sure nothing is muted, I found that with my laptop the headphone jack is actually PC Speakers in alsamixer and I changed that to get it to work. It is possible your problem is similar.

Good idea, but all I've got in there are Master, PCM, and Capture. Should there be other things also? Maybe that's the problem.

---

### Post by drunken-wallaby on 2006-09-19
same problem here, both on dapper as well as on edgy. 

alsamixer just shows master and pcm. 

any suggestion on how to get headphone jack working?

---

### Post by fieldstone on 2006-09-19
> **drunken-wallaby said:**
> same problem here, both on dapper as well as on edgy. 

alsamixer just shows master and pcm. 

any suggestion on how to get headphone jack working?

This is what worked for me. It requires patching and installing ALSA 1.0.12 .


[https://bugtrack.alsa-project.org/al...ew.php?id=2412](https://bugtrack.alsa-project.org/al...ew.php?id=2412)


Basically, you have to install ALSA from the source (get the alsa-driver, alsa-libs, and alsa-utils packages, and install them in that order), patch it, and install it. You can find the source at [http://www.alsa-project.org](http://www.alsa-project.org) (right there in the upper right hand corner of the main page).

Before you install alsa-driver, you'll also have to apply the patch from that link to the file hda_generic.c, which is in the alsa-kernel/pci/hda/ directory inside the extracted alsa-drivers directory (wherever you extract it.

After I did this, I had a separate volume control for my headphone jack, and it worked perfectly. (Installing the alsa-oss and alsa-lib-plugins packages from the ALSA site might also help you with the stability of your sound, but it's not strictly necessary and might also break things, depending on your system.)

If you run AMD64 like I do, extracting the i386 version of the alsa-oss deb file (from [http://packages.ubuntu.com](http://packages.ubuntu.com)) can also help with the stability of sound in 32-bit applications, particularly in Flash.

---

