---
title: "Audacity has no mp3 support"
date: 2009-02-24
forum: General Help
---

### Post by alberto ferreira on 2009-02-24
What the hell, I've upgraded Audacity and now it says that it was compiled with no mp3 support. Already tried to compile it but no-one would help me at the forums so now I cannot manipulate mp3 files and I need it badly!

How can I solve this? thanks for your time

---

### Post by theozzlives on 2009-02-24
Install it from the repos, mine supports MP3. You should go to the repos for software first, you'd be suprized what's in there.

---

### Post by alberto ferreira on 2009-02-27
I had installed audacity from the repos.

It looks like I have audacity 1.3.5 and 1.3.7 installed and in the terminal when I execute the command "audacity" it launches 1.3.7.
I've searched in the PC and to run the prior version I run "/usr/bin/audacity".

1-Is there a way to uninstall 1.3.7?

2-How can I change this behavior so that audacity 1.3.5 gets associated to "audacity" command instead of the latest version(1.3.7)?

---

### Post by geirha on 2009-02-27
audacity apparently uses lame to encode/decode mp3, so check if you have [lame](apt:lame) and [liblame0](apt:liblame0) installed.

---

### Post by oldos2er on 2009-02-27
> **alberto ferreira said:**
> I had installed audacity from the repos.

It looks like I have audacity 1.3.5 and 1.3.7 installed and in the terminal when I execute the command "audacity" it launches 1.3.7.
I've searched in the PC and to run the prior version I run "/usr/bin/audacity".

1-Is there a way to uninstall 1.3.7?

2-How can I change this behavior so that audacity 1.3.5 gets associated to "audacity" command instead of the latest version(1.3.7)?

 Go back into the source code folder, and run 'sudo make uninstall'

---

### Post by alberto ferreira on 2009-02-27
Which source code folder? As I said I had installed it from the repos (with the Synaptic manager) :S

---

### Post by oldos2er on 2009-02-27
You also said "Already tried to compile it". I assumed that's why you have two versions of it.

---

### Post by neu2buntu on 2009-02-27
anytime i have compiled from source it has always upgraded the app . for example lmms from the repos and the latest source ,and ardour against ardourvst. i didnt think it possible to have 2 versions of the same program(app,software) installed ,i wish i could as some new apps are buggy!!!         

im not 100% sure but when an upgrade/update of an app is done the older version still stays on your hd,so the new updated version is still working of the old one..."ALBERTO" you must let us know if the older version had mp3 support before the update or if this is your first attempt...... ... .. . .  i strongly suspect that you dont have the proper repos allowed for mp3 support ... im saying this as i can load mp3 files or mostly any audio files into audacity...propably because i have all the restricted sources allowed...get back and let us know a bit more.....

---

### Post by mc4man on 2009-02-27
Well it certainly does appear you did built and installed 1.3.7 to /usr/local/ (considering there is no repo 1.3.7 for intrepid, and any other available packages (getdeb) would have removed 1.3.5

So in the absence of your build folder go look in /usr/local/ for installed files (bin, lib, share

The orig. location of your build folder
> /home/a/Downloads/audacity-src-1.3.7

---

### Post by mc4man on 2009-02-27
@ neu2buntu
> i didnt think it possible to have 2 versions of the same program(app,software) installed ,i wish i could as some new apps are buggy!!!
While it's possible to install 1 version to /user and another to /usr/local there is a better solution in many cases.

A lot of apps after the make can be run from the build folder without installing. You can make a launcher or give it a .desktop in ~/.local/share/applications, an Applications menu entry and an entry(s) in ~/.local/share/applications/mimeapps.list if desired.

I do it mainly with vlc and mplayer, one revision installed, an other(s) from build folders. (for instance I installed a recent mplayer revision (no dvdnav), and run the same revision with dvdnav enabled from it's folder to fool around with.

---

