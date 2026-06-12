---
title: "How do I make microphone work in recording and in voice chat?"
date: 2009-03-14
forum: General Help
---

### Post by Lingonet on 2009-03-14
Hello!

I have a problem I haven't dealed with yet. I can't record nor chat with a microphone. I stick the microphone in the pink input in the computer but the recording wont work. Neither does it in skype and similar. What should I choose in audio options? And what in standard mixer?

I want to be able to use the microphone!

Thank you!

---

### Post by perrti-y02 on 2009-03-14
Open the sound recorder and then go File>Volume Control. You will probably need to work it out by trial an error but the impression I get is mic boost must be on if it exists and then change each setting in turn. You may have more than one input for your sound card so try switching between them all.
This is one of the things that is really poorly done in Ubuntu.

---

### Post by ProNux on 2009-03-14
Also, when you are in the volume control, go into the OPTIONS tab on top.  Select the MIC option (NOT front mic, if it is there) since yo are using an external mic.

Also I have found out that some (if not, all) these files are needed because I did AUTOREMOVE of the unneeded files but after removing, my Skype won't work, so I reinstalled and restarted.  Check if they are installed, if not, you can try INSTALLING THE FOLLOWING and RESTART.  Don't forget to restart to apply them.

(By the way I am on Ubuntu 8.04, if you are on other versions, I am not sure if they are compatible)


gdk-imlib11
imlib-base
imlib11
libgda3-3
libgda3-common
libgdl-1-0
libgdl-1-common
libgdl-gnome-1-0
libglib1.2ldbl
libgtk1.2
libgtk1.2-common

---

### Post by som24 on 2009-03-26
try this system>preference>sound.there change sound capture to asla.

---

