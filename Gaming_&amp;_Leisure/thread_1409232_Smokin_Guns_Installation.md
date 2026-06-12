---
title: "Smokin Guns Installation"
date: 2010-02-17
forum: Gaming &amp; Leisure
---

### Post by arnab_das on 2010-02-17
I have downloaded the .zip file. Unzipped it, and made the file executable. next when i type "./smokinguns.x86" from the terminal, this is the error i am getting:

```

./smokinguns.x86: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory


```

how do i resolve this issue?

---

### Post by gradinaruvasile on 2010-02-17
What happens if you type:

./smokinguns.i386

?

---

### Post by arnab_das on 2010-02-17
> **gradinaruvasile said:**
> What happens if you type:

./smokinguns.i386

?

[[IMG]http://img697.imageshack.us/img697/6562/screenshot001fl.th.png[/IMG]](http://img697.imageshack.us/i/screenshot001fl.png/)

i cant find any such file. the screenshot is of the files in the folder SmokinGuns.

---

### Post by gradinaruvasile on 2010-02-17
Not sure what version you have...
Here is the latest version:

The game 1.0 version:
[http://wmd.game-host.org/smokin-guns-org/downloads/packages/generic/Smokin_Guns_1.0.zip](http://wmd.game-host.org/smokin-guns-org/downloads/packages/generic/Smokin_Guns_1.0.zip)

And the update to the latest version (just unpack it in the same folder as the previous archive):

[http://www.smokinguns.fr/download/SmokinGuns-1.1b4-update.zip](http://www.smokinguns.fr/download/SmokinGuns-1.1b4-update.zip)

Enjoy!

---

### Post by arnab_das on 2010-02-17
> **gradinaruvasile said:**
> Not sure what version you have...
Here is the latest version:

The game 1.0 version:
[http://wmd.game-host.org/smokin-guns-org/downloads/packages/generic/Smokin_Guns_1.0.zip](http://wmd.game-host.org/smokin-guns-org/downloads/packages/generic/Smokin_Guns_1.0.zip)

And the update to the latest version (just unpack it in the same folder as the previous archive):

[http://www.smokinguns.fr/download/SmokinGuns-1.1b4-update.zip](http://www.smokinguns.fr/download/SmokinGuns-1.1b4-update.zip)

Enjoy!

i did download the .zip file u mentioned there. didnt download the update though. and its version 1.0

dunno if the update is for the game graphics etc.

btw the download link ( [http://www.smokinguns.fr/download/SmokinGuns-1.1b4-update.zip](http://www.smokinguns.fr/download/SmokinGuns-1.1b4-update.zip) )is not mentioned on the official site.

---

### Post by arnab_das on 2010-02-17
incidentally, the .exe installation went smoothly and i can play smokin guns with wine. :)

however would love it if anyone could point out what the problem is.

---

### Post by gradinaruvasile on 2010-02-17
Almost all servers use the newest beta now. So its up for you. 

Here is the original thread:

[http://www.smokin-guns.net/viewtopic.php?t=2079](http://www.smokin-guns.net/viewtopic.php?t=2079)

You will find the update link there. Dont be so paranoid :)

@arnab_das:

Download the 2 archives from the links i posted, extract both archives in the same folder (1.0 first, the beta second) and launch the smokinguns.i386 executable. I play this version of the game and it works.

---

### Post by arnab_das on 2010-02-17
thsnks mate. working perfectly as of now. apart from the audio. which seems to sound more like a vehicle on fire :P

---

### Post by gradinaruvasile on 2010-02-18
> **arnab_das said:**
> thsnks mate. working perfectly as of now. apart from the audio. which seems to sound more like a vehicle on fire :P

Most likely because of PulseAudio. Most (older) Linux games will have this problem. The only resolution is to remove/disable PulseAudio.

BTW i recently switched to Debian testing because of problems such as this.

---

### Post by Perfect Storm on 2010-02-18
Linux 64-bit guide installation for smoking guns: [http://gwos.org/doku.php/guides:64bit:smoking_guns](http://gwos.org/doku.php/guides:64bit:smoking_guns)

---

