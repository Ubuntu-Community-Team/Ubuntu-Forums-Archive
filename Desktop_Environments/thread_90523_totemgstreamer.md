---
title: "totem/gstreamer"
date: 2005-11-15
forum: Desktop Environments
---

### Post by garba on 2005-11-15
perhaps it's just me who's plagued by some odd hardware problem, but I find totem/gstreamer unusable to say the least... high cpu load, audio getting out of sync, no 5.1 support... on the other hand gxine/xine works like a charm... I fear there's something amiss with totem, when playing movies with totem using xine as backend i get no audio output because of the device being "busy"... and as far as I know, I'm not the only one who had similiar experience with the dread totem/gstremer duo... I know gstremear is gnome's default multimedia "backbone", but I can't understand why not provide xine as ubuntu's default out-of-the-box multimedia package, xine proved to be way more reliable and performing... what do you think? regards

---

### Post by frodon on 2005-11-15
I agree, the first thing i did after installing ubuntu is to replace totem-gstreamer by totem-xine and all works fine like that.

---

### Post by tom-ubuntu on 2005-11-15
I agree aswell. I don't use Totem that much, but if I do, I always have at least one problem: Either is crashes, gets out of sync, aso. Memory and CPU usage is hugh aswell.

---

### Post by garba on 2005-11-15
hence it's not just me who's having problems, I hope the ubuntu team will finally understand how important it is to have a setup that works straight out of the box when it comes to multimedia support... but hey, gstreamer is cool, it doesn't matter if it just plain sucks, we gotta make it the default... :rolleyes: not to mention that pathetic ESD being on by default... will we ever get rid of ARTS and ESD and use ALSA's dmix feature one of these days?

---

### Post by linuxrunner on 2005-12-14
i agree totally.
I originally thought it was gstreamer, however, it is indeed totem which cannot sync correctly.  I recently installed kde on my ubuntu system and loaded the same videos into kaffiene(which uses gstreamer) and it ran superbly.  I will say that kde has some great programs, i just which they were more user-oriented.( and this is coming from a 6 year linux user who has no problem admitting that he likes the simplicity of gnome, and the power of the command line) :-)

---

### Post by poptones on 2005-12-14
Hmmmm I thought sound support sucked in hoary, but in breezy I find it works on my nvidia motherboard ootb. it supports multiple sounds and everything and uses esd. I find the latest totem gui better than before, I can actually sort of use it now, though first thing I do is install xine-gui (for playback) and totem-xine (so the thumbnailer works).

---

### Post by nix4me on 2005-12-14
I agree that multimedia is very important and Breezy indeed has issues.

Lets hope Ubuntu can deliver with 6.04.

Linux is doomed if multimedia support isn't up to par.

nix4me

---

### Post by RAOF on 2005-12-14
Well, Dapper is now transitioning to gstreamer 0.10, a big improvement over the 0.8 in Breezy.  The new version should fix all the sync problems, and cure world hunger.

Oh, and the reason why xine isn't used by default is because it's difficult to split the free codecs out of it.

---

