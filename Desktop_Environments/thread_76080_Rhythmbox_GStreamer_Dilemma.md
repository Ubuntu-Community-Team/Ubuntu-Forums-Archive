---
title: "Rhythmbox GStreamer Dilemma"
date: 2005-10-14
forum: Desktop Environments
---

### Post by LinkRJH on 2005-10-14
Well, I followed and posted in the earlier how to play mp3 topic and did everything there...I can't find it, or I'd have added to that one.  Anyways, I got GStreamer like I was told with "sudo apt-get install gstreamer*" and it did it and is done...but I still can't get rhythbox to play any mp3's.  What gives?

Thanks in advance,

Richard

---

### Post by Dr. Nick on 2005-10-14
Im assuming you enabled universe and hit "sudo apt-get update" beofre attempting to install. Mp3s work fine for me.

what error does it give you?

---

### Post by LinkRJH on 2005-10-14
The error is I don't have the proper decoder...and it's probably the fact I know nothing of universe or how to enable it.

---

### Post by Dr. Nick on 2005-10-14
Bingo their is your problem. The mp3 codecs are not in the default repository. 
Here is what you do to get universe.

Run ```
sudo gedit /etc/apt/sources.list
``` and read the file, it should tell you what to do, remove the #'s from the 2 lines it says then run ```
sudo apt-get update
``` then re-run ```
sudo apt-get install gstreamer*
```

You can also use synaptic and go to **Settings - Repositories** and look their to enable universe by hitting the checkbox I believe, just remember the "update" step before attempting to install

---

