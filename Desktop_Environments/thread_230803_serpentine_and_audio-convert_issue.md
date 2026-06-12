---
title: "serpentine and audio-convert issue"
date: 2006-08-06
forum: Desktop Environments
---

### Post by chrsjav on 2006-08-06
Hi,

For some reason, serpentine (used to create audio CDs) fails right after converting the mp3s to WAV, with the "couldn't convert all files" error. I've used serpentine before, so this was really strange. 

I really doubt it's a codec issue. Not only can rhythmbox and banshee play mp3s, but whenever I hover over a mp3, nautilus will play it too.

So in frustration I installed K3b, only to find it can't find/use the codecs I already have... ](*,) 

My next plan was to convert everything to WAV manually, then see if serpentine/K3b can handle it. I installed the nautilus-scripts-audio-convert package with aptitude, but even after restarting GDM, I found no script in the right-click menu. In fact the nautilus script folder inside .gnome2 is empty.

I can install the script manually, but I thought perhaps the community had some idea as to why the ubuntu gods have frowned upon me today. Could it be initng?

---

### Post by croak77 on 2006-08-06
Try soundconverter, It's in the repo's and uses gstreamer.

---

### Post by chrsjav on 2006-08-10
gnomebaker and soundconverter both use gstreamer0.8.

The problem with my audio is that its not 16-bit, stereo, 44.1kHz... Is there  a way to convert without gstreamer0.8?

Thanks

---

