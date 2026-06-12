---
title: "Image Viewer &quot;Set As Wallpaper&quot; not working properly"
date: 2007-03-29
forum: Desktop Environments
---

### Post by Ubunthree on 2007-03-29
Something has changed with the interaction between the "Eye of Gnome" image viewer and the Desktop Background Preferences dialog on my Ubuntu system. When I open an image in the viewer, and choose Image/Set As Wallpaper, the Background Preferences box opens as it should, but the image is no longer automatically set as the background, or even added to the list of available backgrounds. I have to go through the "Add Wallpaper" process anyway, to find the image file and select it. I had to [COLOR="DarkRed"]sudo dpkg --configure -a[/COLOR] to clean up the fallout - missing dependencies I think -from an interrupted update download a couple of days ago, which was causing the lower panel's Window List item to not display properly. I don't know whether this happened at the same time, or is related, or not.

Thanks for any help!

---

### Post by ComplexNumber on 2007-03-29
personally, i would't have thought that they were related. although i could be wrong because i don't know all the details. i really wouldnt have thought so, though.

i've just tried out eye of gnome, and it behaves as it should. i'm baffled as to why its not working correctly for you. i would hazard at a guess that its something wrong with the installation. i can't see any settings that may possibly cause the behaviour that you report.

have you tried uninstalling it completely in synaptic, then reinstalling it?

---

### Post by Ubunthree on 2007-03-30
> **ComplexNumber said:**
> personally, i would't have thought that they were related. although i could be wrong because i don't know all the details. i really wouldnt have thought so, though.

Thanks for the quick reply. I was thinking that maybe the glitchy update had dropped something else besides what was apparently covered by my earlier fix.

> **ComplexNumber said:**
> ...have you tried uninstalling it completely in synaptic, then reinstalling it?

I found it in Synaptic and did just a reinstallation, which didn't fix anything. Synaptic says that actually removing it will require also removing ubuntu-desktop, which sounds like something I don't want to mess with, but then I'm pretty much a noob here, so I don't know. I marked ubuntu-desktop for reinstallation also, did that, and restarted Gnome, but it didn't help either.

---

### Post by ComplexNumber on 2007-04-01
> Synaptic says that actually removing it will require also removing ubuntu-desktop, which sounds like something I don't want to mess with
don't worry abut that. ubuntu-desktop is merely a metapackage. removing it doesn't affect anything else whatsoever.

---

### Post by yabbadabbadont on 2007-04-01
> **ComplexNumber said:**
> don't worry abut that. ubuntu-desktop is merely a metapackage. removing it doesn't affect anything else whatsoever.

Unless you accidentally use the autoremove option later...  ;)

(I helped someone who did just that a while back.)

---

### Post by Ubunthree on 2007-04-02
Ok, I marked "eog" for complete removal, dragging ubuntu-desktop down with it. CTRL/ALT/Backspaced to restart Gnome. Reinstalled eog and ubuntu-desktop. Wallpaper selection is still broken as before. So this isn't a huge deal as far as using Ubuntu goes, but I always like to know why things happen, and I guess I have a puzzle to work on. Thanks for the ideas anyway!

---

### Post by Ubunthree on 2007-04-06
Still haven't figured out what the eog issue is, but I've switched to gThumb now, the wallpaper function of which seems to work fine. Now the panel clock is twelve hours off, and the adjustment routine won't start, so I have to start another thread for that. ::sigh::

---

